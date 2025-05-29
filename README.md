# Custom Heroku Ruby Buildpack (Ruby 2.6.6 + Bundler 1.17.3)

This buildpack installs Ruby 2.6.6 and Bundler 1.17.3 regardless of Heroku stack. Use it if you need to deploy legacy Ruby apps on stacks that do not support Ruby <3.1 (e.g., Heroku-24).

## Usage

1. Add this buildpack to your Heroku app:

   ```sh
   heroku buildpacks:set https://github.com/your-username/heroku-ruby6-buildpack
   ```

2. Deploy your app as usual. This buildpack will force Ruby 2.6.6 and Bundler 1.17.3.

## Notes
- This buildpack downloads the Ruby 2.6.6 binary from Heroku's legacy S3. If it fails, you must provide a compatible binary for your stack.
- No other checks or version logic are included.
