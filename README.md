# ShotgunDropper for Hiero!

## Installation Instructions
# Step 1. Tank Install
Run the following tank command:

    tank install_app project tk-hiero https://github.com/RicardoMusch/rtm-tk-hiero-shotgunDropper.git

This should retrieve the latest Git release.

# Step 2. Edit app_locations.yml
Since Shotgun updated their config2 yaml file layouts tank cannot install apps completely by itself (this may be fixed in the future, lets hope so!).
So we'll do it manually for now!

Navigate to the folowing location and open this file:

    <project_config>/env/includes/app_locations.yml

Then add the following app to this config:

    apps.rtm-tk-hiero-shotgunDropper.location:
      type: git
      path: https://github.com/RicardoMusch/rtm-tk-hiero-shotgunDropper.git
      version: v0.1


# Step 3. Edit tk-nuke.yml
Edit tk-nuke which is apparently also used for Hiero settings.
Find the Nuke Project config, it loks like this:

    settings.tk-nuke.hiero.project:
      apps:

Add the following lines to the above app configuration:

    settings.rtm-tk-hiero-shotgunDropper:
      location: "@apps.rtm-tk-hiero-shotgunDropper.location"

## Updates
Updating the app.

Check Github for the latest release tag.
Then edit the app_locations.yml file version tag.
Then run the following tank command:

    tank cache_apps

