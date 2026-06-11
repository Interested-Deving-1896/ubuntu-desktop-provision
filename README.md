[update-readmes]   Mode: rewrite — migrating to template structure...
# ubuntu-desktop-provision

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/ubuntu-desktop-provision)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/ubuntu-desktop-provision.git
cd ubuntu-desktop-provision
```

## Usage

<!-- Add usage examples here. This section is yours — the AI will not modify it. -->

## Configuration


The full configuration guide can be read [here](https://docs.google.com/document/d/10R0YOj4e8BTv6XPw9OE_y7GDy72xPqA5XP5lu0M7VbE/edit?usp=sharing).

But the basics are that the UI can be configured using a [YAML](https://yaml.org/) file that is read from here:
`/usr/share/desktop-provision/whitelabel.yaml`

The configuration file has the following structure:

```yaml
# (Optional) Drives overall behavior for specific provisioners.
#
# Options:
# - standard (default): the common provision flow for Ubuntu Desktop and Flavors
# - oem: enables the eula page and disables the user creation page during bootstrap
# - core-desktop: disables exiting the installer at the end (because there is no
#   live session), and only allows to reboot
mode: standard | oem | core-desktop

# (Optional) When set, the light and dark theme is inherited from ubuntu-flutter-plugins and the distro name is set.
#
# Options:
# - budgie
# - cinnamon
# - edubuntu
# - kubuntu
# - kylin
# - lubuntu
# - mate
# - studio
# - unity
# - xubuntu
flavor: <name>

# (Optional) Sets the window's title (e.g. the text in alt|super + tab)
app-name: <string>

# (Optional) Overrides the theme's accent colors (remember the quotes)
theme:
  light:
    accent-color: <color-hex-code> # i.e. "#ff0011"
    elevated-button-color: <color-hex-code>
    elevated-button-text-color: <color-hex-code>
  dark:
    accent-color: <color-hex-code> # i.e. "#ff0011"
    elevated-button-color: <color-hex-code>
    elevated-button-text-color: <color-hex-code>

# (Optional) Override a page's image asset and whether they should be shown or not.
# Images expected in /usr/share/desktop-provision/images/<image-name>
#
# Bootstrap pages:
# - locale: Select the interface language
# - accessibility: Allow user to configure GNOME accessibility options
# - try-or-install: Choose between trying the live session or installing (only shown when --try-or-install is passed)
# - rst: Identifies if the computer has Intel Rapid Storage Technology (rst) active
# - keyboard: Set keyboard layout
# - network: Connect to a network
# - refresh: Expose installer's auto-update mechanism
# - source-selection: Choose installation source, i.e. which applications that should be installed
# - codecs-and-drivers: Choose if proprietary codecs and drivers should be installed
# - not-enough-disk-space: Notifies if there is insufficient disk space
# - secure-boot: Handles secure boot
# - storage: Select target disk and partition
# - storage-icon: Not a separate page, but sets the distribution icon on the storage page
# - identity: Create the first-user account (only displayed if mode = default)
# - confirm: A summary of the installation and confirmation button to start the install
# - done: Choose whether to restart or continue testing in the live session
# - error: The page that shows when something goes wrong
#
# Init pages (for oem only)
# - identity: Create the first-user account
# - ubuntu-pro-onboarding: Enable Ubuntu Pro
# - eula: Accept the OEM provided EULA
# - privacy: Enable location services
# - timezone: Set the timezone
# - telemetry: Enable sending telemetry
#
# Do note that currently only ubuntu-pro-onboarding, eula, accessibility, try-or-install, refresh and source-selection can be hidden.
pages:
  <page-name>:
    image: <image-name>
    image-dark: <dark-image-name>
    visible: <bool>
```

### Custom Slides

To customize the slides that are shown while the installation is underway you just need to add a slides directory in
`/usr/share/desktop-provision/slides` and add numbered subdirectories with localized html-files and image files in
there. The numbers determine in which order the slides should be.

An example structure could look like this:

```
/usr/share/desktop-provision
└── slides
   ├── 1
   │   ├── animal.svg
   │   ├── slide_de_DE.svg
   │   ├── slide_en_US.svg
   │   ├── slide_sv_FI.svg
   │   └── slide_sv_SE.html
   ├── 2
   │   ├── slide_en_US.html
   │   └── store.png
   └── 3
       ├── slide_en_US.html
       └── vscode.png
```

If the locale that the user currently is using doesn't have a corresponding html file it will fall back to
`slide_en_US.html`. See the [Language code format section](#language-code-format) for further details about the language
code format.

Do note that the HTML supported in these “html” files is far from the full standard, so we recommend that you use one of
the templates provided as the default slides:
https://github.com/canonical/ubuntu-desktop-provision/tree/main/packages/ubuntu_bootstrap/assets/slides

### EULA

EULA assets are expected to reside in `/usr/share/desktop-provision/eula/` with the file name including the language
code: EULA_<langcode>.pdf. If the <langcode> is not available, the default file EULA.pdf will be used.
The language code format is the same as is used for slides, for example: EULA_en_US.pdf, see the [Language code format
section](#language-code-format) for further details,

### Language code format

The language code format that is used is the two-letter language code followed by a two-letter country code
(see the ISO 639-1 and ISO 3166-1 standards). The language code represents the primary language, while the country code
specifies the regional or national variant of that language. For example en_US represents American English and pt_BR
represents Brazilian Portuguese.

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/ubuntu-desktop-provision`](https://github.com/Interested-Deving-1896/ubuntu-desktop-provision) and mirrored through:

```
Interested-Deving-1896/ubuntu-desktop-provision  ──►  OpenOS-Project-OSP/ubuntu-desktop-provision  ──►  OpenOS-Project-Ecosystem-OOC/ubuntu-desktop-provision
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
[GPL-3.0](https://github.com/Interested-Deving-1896/ubuntu-desktop-provision/blob/main/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
