homebrew-virt-manager
=====================

A set of [homebrew][homebrew] formulae to install [`virt-manager`][virt-manager] and [`virt-viewer`][virt-viewer] on Mac OSX. This repo installs the latest version of virt-manager and virt-viewer which contains meson/ninja build system. Previous versions of virt-manager and virt-viewer used configure and make for building

## Usage

    brew tap muxneo/homebrew-virt-manager
    brew install muxneo/homebrew-virt-manager/virt-manager muxneo/homebrew-virt-manager/virt-viewer
    virt-manager -c test:///default

## FAQs

#### Why can't I connect to a remote URI?

When connecting to remote URIs, you probably need to override the `libvirt` socket location, see [www.jedi.be][jedi].

    virt-manager -c 'qemu+ssh://user@libvirthost/system?socket=/var/run/libvirt/libvirt-sock'
    virt-viewer -c 'qemu+ssh://user@libvirthost/system?socket=/var/run/libvirt/libvirt-sock'

#### I still can't connect to a remote URI, why?

This formula for `virt-manager` does not include the `openssh-askpass` dependency and does not prompt for passwords in a popup window. Here are two workarounds:

1. Run `virt-manager` with either the `--debug` or `--no-fork` option to get password prompt via the CLI.

2. Set up SSH keys between your local and remote system to avoid the prompt.


#### Everything was working yesterday, but it's not working today, can you help?

If `virt-manager` or its dependencies have been upgraded recently (`brew upgrade`), it's possible that a reinstall may fix the issue 

[homebrew]: http://brew.sh/
[virt-manager]: https://virt-manager.org/
[virt-viewer]: https://virt-manager.org/
[jedi]: http://www.jedi.be/blog/2011/09/13/libvirt-fog-provider/#macosx-remote-libvirt-client-
