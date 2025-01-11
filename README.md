# Storm 2 Public SDK

Be sure to check out the [Wiki](https://github.com/stormsoftwarenet/storm2-example-plugin/wiki) as well to get help setting up your development environment.

## How to create a token
Below is a short explanation on how to create a GitHub Personal Access token to download the dependencies

Follow these steps:

1. Log in to your GitHub account and navigate to Settings.
2. In the left sidebar, click on "Developer settings" and then select "Fine-grained tokens" under "Personal access tokens".
3. Click on "Generate new token".
4. Provide a descriptive name for your token in the "Token name" field.
5. Set an expiration date for the token.
6. Click "Generate token" at the bottom of the page.
7. Copy the generated token immediately and store it securely, as you won't be able to see it again.

Once you have your personal access token, you can use it to authenticate and download the Maven packages.

## How to use in example-plugins (Gradle) project
The referenced example plugin project can be found [here](https://github.com/stormsoftwarenet/storm2-example-plugin)
1. Navigate to the build.gradle.kts file
2. Look for the following [code block](https://github.com/stormsoftwarenet/storm2-example-plugin/blob/4eb17e155dc52dda3d858be5681358166bfdf875/build.gradle.kts#L34):
```
maven {
    url = uri("https://maven.pkg.github.com/stormsoftwarenet/storm2-public-sdk")
    authentication {
        create<BasicAuthentication>("basic")
    }
    credentials {
        username = ""
        password = System.getenv("GITHUB_PACKAGES_PAT")
    }
}
```
3. Either store the token you have just created in an Environment Variable called `GITHUB_PACKAGES_PAT`, OR replace the `System.getenv("GITHUB_PACKAGES_PAT")` with your token as a string. (NOT RECOMMENDED!)
  
Your IDE will now download the dependencies when needed, before compilation.
