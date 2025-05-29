# Custom Heroku Ruby Buildpack (Ruby 2.6.6 + Bundler 1.17.3)

This buildpack installs Ruby 2.6.6 and Bundler 1.17.3 regardless of Heroku stack. Use it if you need to deploy legacy Ruby apps on stacks that do not support Ruby <3.1 (e.g., Heroku-24).

## Usage

1. Add this buildpack to your Heroku app:

   ```sh
   heroku buildpacks:set https://github.com/abhilashiig/heroku-ruby6-buildpack
   ```

2. Deploy your app as usual. This buildpack will force Ruby 2.6.6 and Bundler 1.17.3.

## Features

- Primarily uses the official Ruby source from ruby-lang.org
- Compiles Ruby 2.6.6 from source with minimal dependencies
- Falls back to pre-compiled binaries if compilation fails
- Caches compiled Ruby for faster subsequent builds
- Verifies Ruby and Bundler installations before proceeding
- Detailed logging for easier debugging

## How It Works

This buildpack:

1. Attempts to use a cached compiled version of Ruby 2.6.6 if available
2. If no cached version exists, downloads the official Ruby 2.6.6 source from ruby-lang.org
3. Checks for essential build tools (gcc, make, autoconf)
4. Configures Ruby with minimal dependencies to avoid reliance on system packages
5. Compiles Ruby from source with optimized settings
6. If compilation fails, falls back to pre-compiled Heroku binaries
7. Caches the Ruby installation for future builds
8. Verifies the Ruby installation is working correctly
9. Installs Bundler 1.17.3
10. Configures the application with the correct Ruby and Bundler settings
11. Installs dependencies using Bundler

## Troubleshooting

If you encounter issues:

- Check the build logs for detailed error messages
- Review the Ruby compilation logs (`ruby-configure.log`, `ruby-make.log`, and `ruby-install.log`) in your build directory
- Ensure your `Gemfile` and `Gemfile.lock` are compatible with Ruby 2.6.6 and Bundler 1.17.3
- If the build is taking too long, subsequent builds will be faster due to caching
- For compilation issues, you may need to add specific build dependencies to your app
