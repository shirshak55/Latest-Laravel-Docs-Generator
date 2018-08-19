# HTTP Tests {#http-tests}

- [Introduction](#http-tests-introduction)
    - [Customizing Request Headers](#http-tests-customizing-request-headers)
- [Session / Authentication](#http-tests-session-and-authentication)
- [Testing JSON APIs](#http-tests-testing-json-apis)
- [Testing File Uploads](#http-tests-testing-file-uploads)
- [Available Assertions](#http-tests-available-assertions)
    - [Response Assertions](#http-tests-response-assertions)
    - [Authentication Assertions](#http-tests-authentication-assertions)

## Introduction {#http-tests-introduction}

Laravel provides a very fluent API for making HTTP requests to your application and examining the output. For example, take a look at the test defined below:

    <?php

    namespace Tests\Feature;

    use Tests\TestCase;
    use Illuminate\Foundation\Testing\RefreshDatabase;
    use Illuminate\Foundation\Testing\WithoutMiddleware;

    class ExampleTest extends TestCase
    {
        /**
         * A basic test example.
         *
         * @return void
         */
        public function testBasicTest()
        {
            $response = $this->get('/');

            $response->assertStatus(200);
        }
    }

The `get` method makes a `GET` request into the application, while the `assertStatus` method asserts that the returned response should have the given HTTP status code. In addition to this simple assertion, Laravel also contains a variety of assertions for inspecting the response headers, content, JSON structure, and more.

### Customizing Request Headers {#http-tests-customizing-request-headers}

You may use the `withHeaders` method to customize the request's headers before it is sent to the application. This allows you to add any custom headers you would like to the request:

    <?php

    class ExampleTest extends TestCase
    {
        /**
         * A basic functional test example.
         *
         * @return void
         */
        public function testBasicExample()
        {
            $response = $this->withHeaders([
                'X-Header' => 'Value',
            ])->json('POST', '/user', ['name' => 'Sally']);

            $response
                ->assertStatus(201)
                ->assertJson([
                    'created' => true,
                ]);
        }
    }

> {tip} The CSRF middleware is automatically disabled when running tests.

## Session / Authentication {#http-tests-session-and-authentication}

Laravel provides several helpers for working with the session during HTTP testing. First, you may set the session data to a given array using the `withSession` method. This is useful for loading the session with data before issuing a request to your application:

    <?php

    class ExampleTest extends TestCase
    {
        public function testApplication()
        {
            $response = $this->withSession(['foo' => 'bar'])
                             ->get('/');
        }
    }

Of course, one common use of the session is for maintaining state for the authenticated user. The `actingAs` helper method provides a simple way to authenticate a given user as the current user. For example, we may use a [model factory](#{{version}}/database-testing-writing-factories) to generate and authenticate a user:

    <?php

    use App\User;

    class ExampleTest extends TestCase
    {
        public function testApplication()
        {
            $user = factory(User::class)->create();

            $response = $this->actingAs($user)
                             ->withSession(['foo' => 'bar'])
                             ->get('/');
        }
    }

You may also specify which guard should be used to authenticate the given user by passing the guard name as the second argument to the `actingAs` method:

    $this->actingAs($user, 'api')

## Testing JSON APIs {#http-tests-testing-json-apis}

Laravel also provides several helpers for testing JSON APIs and their responses. For example, the `json`, `get`, `post`, `put`, `patch`, and `delete` methods may be used to issue requests with various HTTP verbs. You may also easily pass data and headers to these methods. To get started, let's write a test to make a `POST` request to `/user` and assert that the expected data was returned:

    <?php

    class ExampleTest extends TestCase
    {
        /**
         * A basic functional test example.
         *
         * @return void
         */
        public function testBasicExample()
        {
            $response = $this->json('POST', '/user', ['name' => 'Sally']);

            $response
                ->assertStatus(201)
                ->assertJson([
                    'created' => true,
                ]);
        }
    }

> {tip} The `assertJson` method converts the response to an array and utilizes `PHPUnit::assertArraySubset` to verify that the given array exists within the JSON response returned by the application. So, if there are other properties in the JSON response, this test will still pass as long as the given fragment is present.

### Verifying An Exact JSON Match {#http-tests-verifying-exact-match}

If you would like to verify that the given array is an **exact** match for the JSON returned by the application, you should use the `assertExactJson` method:

    <?php

    class ExampleTest extends TestCase
    {
        /**
         * A basic functional test example.
         *
         * @return void
         */
        public function testBasicExample()
        {
            $response = $this->json('POST', '/user', ['name' => 'Sally']);

            $response
                ->assertStatus(201)
                ->assertExactJson([
                    'created' => true,
                ]);
        }
    }

## Testing File Uploads {#http-tests-testing-file-uploads}

The `Illuminate\Http\UploadedFile` class provides a `fake` method which may be used to generate dummy files or images for testing. This, combined with the `Storage` facade's `fake` method greatly simplifies the testing of file uploads. For example, you may combine these two features to easily test an avatar upload form:

    <?php

    namespace Tests\Feature;

    use Tests\TestCase;
    use Illuminate\Http\UploadedFile;
    use Illuminate\Support\Facades\Storage;
    use Illuminate\Foundation\Testing\RefreshDatabase;
    use Illuminate\Foundation\Testing\WithoutMiddleware;

    class ExampleTest extends TestCase
    {
        public function testAvatarUpload()
        {
            Storage::fake('avatars');

            $file = UploadedFile::fake()->image('avatar.jpg');

            $response = $this->json('POST', '/avatar', [
                'avatar' => $file,
            ]);

            // Assert the file was stored...
            Storage::disk('avatars')->assertExists($file->hashName());

            // Assert a file does not exist...
            Storage::disk('avatars')->assertMissing('missing.jpg');
        }
    }

#### Fake File Customization

When creating files using the `fake` method, you may specify the width, height, and size of the image in order to better test your validation rules:

    UploadedFile::fake()->image('avatar.jpg', $width, $height)->size(100);

In addition to creating images, you may create files of any other type using the `create` method:

    UploadedFile::fake()->create('document.pdf', $sizeInKilobytes);

## Available Assertions {#http-tests-available-assertions}

### Response Assertions {#http-tests-response-assertions}

Laravel provides a variety of custom assertion methods for your [PHPUnit](https://phpunit.de/) tests. These assertions may be accessed on the response that is returned from the `json`, `get`, `post`, `put`, and `delete` test methods:

<style>
    .collection-method-list > p {
        column-count: 3; -moz-column-count: 3; -webkit-column-count: 3;
        column-gap: 2em; -moz-column-gap: 2em; -webkit-column-gap: 2em;
    }

    .collection-method-list a {
        display: block;
    }
</style>

<div class="collection-method-list" markdown="1">

[assertCookie](#http-tests-assert-cookie)
[assertCookieExpired](#http-tests-assert-cookie-expired)
[assertCookieNotExpired](#http-tests-assert-cookie-not-expired)
[assertCookieMissing](#http-tests-assert-cookie-missing)
[assertDontSee](#http-tests-assert-dont-see)
[assertDontSeeText](#http-tests-assert-dont-see-text)
[assertExactJson](#http-tests-assert-exact-json)
[assertForbidden](#http-tests-assert-forbidden)
[assertHeader](#http-tests-assert-header)
[assertHeaderMissing](#http-tests-assert-header-missing)
[assertJson](#http-tests-assert-json)
[assertJsonCount](#http-tests-assert-json-count)
[assertJsonFragment](#http-tests-assert-json-fragment)
[assertJsonMissing](#http-tests-assert-json-missing)
[assertJsonMissingExact](#http-tests-assert-json-missing-exact)
[assertJsonStructure](#http-tests-assert-json-structure)
[assertJsonValidationErrors](#http-tests-assert-json-validation-errors)
[assertLocation](#http-tests-assert-location)
[assertNotFound](#http-tests-assert-not-found)
[assertOk](#http-tests-assert-ok)
[assertPlainCookie](#http-tests-assert-plain-cookie)
[assertRedirect](#http-tests-assert-redirect)
[assertSee](#http-tests-assert-see)
[assertSeeInOrder](#http-tests-assert-see-in-order)
[assertSeeText](#http-tests-assert-see-text)
[assertSeeTextInOrder](#http-tests-assert-see-text-in-order)
[assertSessionHas](#http-tests-assert-session-has)
[assertSessionHasAll](#http-tests-assert-session-has-all)
[assertSessionHasErrors](#http-tests-assert-session-has-errors)
[assertSessionHasErrorsIn](#http-tests-assert-session-has-errors-in)
[assertSessionHasNoErrors](#http-tests-assert-session-has-no-errors)
[assertSessionMissing](#http-tests-assert-session-missing)
[assertStatus](#http-tests-assert-status)
[assertSuccessful](#http-tests-assert-successful)
[assertViewHas](#http-tests-assert-view-has)
[assertViewHasAll](#http-tests-assert-view-has-all)
[assertViewIs](#http-tests-assert-view-is)
[assertViewMissing](#http-tests-assert-view-missing)

</div>

#### assertCookie {#http-tests-assert-cookie}

Assert that the response contains the given cookie:

    $response->assertCookie($cookieName, $value = null);

#### assertCookieExpired {#http-tests-assert-cookie-expired}

Assert that the response contains the given cookie and it is expired:

    $response->assertCookieExpired($cookieName);

#### assertCookieNotExpired {#http-tests-assert-cookie-not-expired}

Assert that the response contains the given cookie and it is not expired:

    $response->assertCookieNotExpired($cookieName);

#### assertCookieMissing {#http-tests-assert-cookie-missing}

Assert that the response does not contains the given cookie:

    $response->assertCookieMissing($cookieName);

#### assertDontSee {#http-tests-assert-dont-see}

Assert that the given string is not contained within the response:

    $response->assertDontSee($value);

#### assertDontSeeText {#http-tests-assert-dont-see-text}

Assert that the given string is not contained within the response text:

    $response->assertDontSeeText($value);

#### assertExactJson {#http-tests-assert-exact-json}

Assert that the response contains an exact match of the given JSON data:

    $response->assertExactJson(array $data);

#### assertForbidden {#http-tests-assert-forbidden}

Assert that the response has a forbidden status code:

    $response->assertForbidden();

#### assertHeader {#http-tests-assert-header}

Assert that the given header is present on the response:

    $response->assertHeader($headerName, $value = null);

#### assertHeaderMissing {#http-tests-assert-header-missing}

Assert that the given header is not present on the response:

    $response->assertHeaderMissing($headerName);

#### assertJson {#http-tests-assert-json}

Assert that the response contains the given JSON data:

    $response->assertJson(array $data);

#### assertJsonCount {#http-tests-assert-json-count}

Assert that the response JSON has an array with the expected number of items at the given key:

    $response->assertJsonCount($count, $key = null);

#### assertJsonFragment {#http-tests-assert-json-fragment}

Assert that the response contains the given JSON fragment:

    $response->assertJsonFragment(array $data);

#### assertJsonMissing {#http-tests-assert-json-missing}

Assert that the response does not contain the given JSON fragment:

    $response->assertJsonMissing(array $data);

#### assertJsonMissingExact {#http-tests-assert-json-missing-exact}

Assert that the response does not contain the exact JSON fragment:

    $response->assertJsonMissingExact(array $data);

#### assertJsonStructure {#http-tests-assert-json-structure}

Assert that the response has a given JSON structure:

    $response->assertJsonStructure(array $structure);

#### assertJsonValidationErrors {#http-tests-assert-json-validation-errors}

Assert that the response has the given JSON validation errors for the given keys:

    $response->assertJsonValidationErrors($keys);

#### assertLocation {#http-tests-assert-location}

Assert that the response has the given URI value in the `Location` header:

    $response->assertLocation($uri);

#### assertNotFound {#http-tests-assert-not-found}

Assert that the response has a not found status code:

    $response->assertNotFound();

#### assertOk {#http-tests-assert-ok}

Assert that the response has a 200 status code:

    $response->assertOk();

#### assertPlainCookie {#http-tests-assert-plain-cookie}

Assert that the response contains the given cookie (unencrypted):

    $response->assertPlainCookie($cookieName, $value = null);

#### assertRedirect {#http-tests-assert-redirect}

Assert that the response is a redirect to a given URI:

    $response->assertRedirect($uri);

#### assertSee {#http-tests-assert-see}

Assert that the given string is contained within the response:

    $response->assertSee($value);

#### assertSeeInOrder {#http-tests-assert-see-in-order}

Assert that the given strings are contained in order within the response:

    $response->assertSeeInOrder(array $values);

#### assertSeeText {#http-tests-assert-see-text}

Assert that the given string is contained within the response text:

    $response->assertSeeText($value);

#### assertSeeTextInOrder {#http-tests-assert-see-text-in-order}

Assert that the given strings are contained in order within the response text:

    $response->assertSeeTextInOrder(array $values);

#### assertSessionHas {#http-tests-assert-session-has}

Assert that the session contains the given piece of data:

    $response->assertSessionHas($key, $value = null);

#### assertSessionHasAll {#http-tests-assert-session-has-all}

Assert that the session has a given list of values:

    $response->assertSessionHasAll(array $data);

#### assertSessionHasErrors {#http-tests-assert-session-has-errors}

Assert that the session contains an error for the given field:

    $response->assertSessionHasErrors(array $keys, $format = null, $errorBag = 'default');

#### assertSessionHasErrorsIn {#http-tests-assert-session-has-errors-in}

Assert that the session has the given errors:

    $response->assertSessionHasErrorsIn($errorBag, $keys = [], $format = null);

#### assertSessionHasNoErrors {#http-tests-assert-session-has-no-errors}

Assert that the session has no errors:

    $response->assertSessionHasNoErrors();

#### assertSessionMissing {#http-tests-assert-session-missing}

Assert that the session does not contain the given key:

    $response->assertSessionMissing($key);

#### assertStatus {#http-tests-assert-status}

Assert that the response has a given code:

    $response->assertStatus($code);

#### assertSuccessful {#http-tests-assert-successful}

Assert that the response has a successful status code:

    $response->assertSuccessful();

#### assertViewHas {#http-tests-assert-view-has}

Assert that the response view was given a piece of data:

    $response->assertViewHas($key, $value = null);

#### assertViewHasAll {#http-tests-assert-view-has-all}

Assert that the response view has a given list of data:

    $response->assertViewHasAll(array $data);

#### assertViewIs {#http-tests-assert-view-is}

Assert that the given view was returned by the route:

    $response->assertViewIs($value);

#### assertViewMissing {#http-tests-assert-view-missing}

Assert that the response view is missing a piece of bound data:

    $response->assertViewMissing($key);

### Authentication Assertions {#http-tests-authentication-assertions}

Laravel also provides a variety of authentication related assertions for your [PHPUnit](https://phpunit.de/) tests:

Method  | Description
------------- | -------------
`$this->assertAuthenticated($guard = null);`  |  Assert that the user is authenticated.
`$this->assertGuest($guard = null);`  |  Assert that the user is not authenticated.
`$this->assertAuthenticatedAs($user, $guard = null);`  |  Assert that the given user is authenticated.
`$this->assertCredentials(array $credentials, $guard = null);`  |  Assert that the given credentials are valid.
`$this->assertInvalidCredentials(array $credentials, $guard = null);`  |  Assert that the given credentials are invalid.
