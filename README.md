# Custom Heroku Ruby Buildpack (Ruby 2.6.6 + Bundler 1.17.3)

This buildpack installs Ruby 2.6.6 and Bundler 1.17.3 regardless of Heroku stack. Use it if you need to deploy legacy Ruby apps on stacks that do not support Ruby <3.1 (e.g., Heroku-24).

## Usage

1. Add this buildpack to your Heroku app:

   ```sh
   heroku buildpacks:set https://github.com/abhilashiig/heroku-ruby6-buildpack
   ```

2. Deploy your app as usual. This buildpack will force Ruby 2.6.6 and Bundler 1.17.3.

## Features

- Compatible with Heroku-24, Heroku-22, Heroku-20, and Cedar-14 stacks
- Tries multiple Ruby binary sources to ensure compatibility
- Caches Ruby installation for faster subsequent builds
- Verifies Ruby and Bundler installations before proceeding
- Detailed logging for easier debugging

## How It Works

This buildpack:

1. Attempts to download Ruby 2.6.6 from multiple Heroku S3 sources
2. Caches the Ruby binary for future builds
3. Verifies the Ruby installation is working correctly
4. Installs Bundler 1.17.3
5. Configures the application with the correct Ruby and Bundler settings
6. Installs dependencies using Bundler

## Troubleshooting

If you encounter issues:

- Check the build logs for detailed error messages
- Ensure your `Gemfile` and `Gemfile.lock` are compatible with Ruby 2.6.6 and Bundler 1.17.3
- If Ruby binary download fails, the buildpack will try alternative sources
