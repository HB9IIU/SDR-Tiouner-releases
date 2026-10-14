# Documentation review — 14 October 2026

Scope: README.md, SOURCE-OFFER.txt, LICENSE and local image references. The published v0.1.0-beta.1 binary archive was downloaded and inspected without executing it. Application source is not available in this checkout, so runtime behaviour remains unverified.

## Corrections made

- Corrected the receive chain to the QO-100 wideband DATV transponder and specified the 741–749 MHz IF for a 9750 MHz LNB local oscillator. Reference: [AMSAT-DL bandplan](https://amsat-dl.org/en/p4-a-wb-transponder-bandplan-and-operating-guidelines/).
- Distinguished sample rate (MS/s) from symbol rate (MSym/s), and defined “full band”.
- Removed CPU age as a guarantee of AVX2 support.
- Clarified that free redistribution is the author's preference, not an additional licence condition.
- Pointed to the actual repository LICENSE and distinguished repository files from binary-package files.
- Verified that root-level third-party licence files and licenses/ both exist in the archive. The earlier suggestion that these locations conflicted was incorrect.
- Replaced the ambiguous October 2026 source-request identifier with the exact version and archive filename.
- Qualified the Pluto network claim: the standard ADALM-Pluto has USB 2.0, and Ethernet adapters use its USB host interface. A Gigabit adapter does not establish sustained full-band throughput. References: [hardware specifications](https://www.analog.com/en/resources/evaluation-hardware-and-software/evaluation-boards-kits/adalm-pluto.html), [USB host support](https://wiki.analog.com/university/tools/pluto/usb_otg_host_function_support).

## Open findings

1. **Source distribution needs resolution before release.** The documents offer source only on request. For binaries downloaded from a designated place, GPLv3 section 6(d) calls for equivalent access to Corresponding Source through the same place (a different server may be used with clear directions). The written-offer route in section 6(b) concerns physical products/media and has its own duration requirements. Publish the exact corresponding source archive, including required build scripts and covered dependencies, and link it beside each binary release. The existing offer's “three years ... as long as this version is distributed” wording should not be treated as proof of compliance. This review does not establish that the release meets all licence obligations. Reference: [GPLv3 section 6](https://www.gnu.org/licenses/gpl-3.0.html#section6).
2. **Package inventory verified; download name corrected.** The asset is SDR-Tiouner-0.1.0-beta.1-windows-x64.zip, not SDR-Tiouner-windows-x64.zip. It contains SDR-Tiouner.exe, Start SDR-Tiouner.cmd, LICENSE.txt, SOURCE-OFFER.txt, THIRD-PARTY-NOTICES.txt, root-level component licences and licenses/. LICENSE.txt matches repository LICENSE after newline normalization. This verifies their presence, not licence completeness for every dependency.
3. **Hardware claims need application-specific evidence.** Confirm supported SDRplay models, sustained bandwidth figures, LimeSDR USB 2 performance, Pluto throughput, and RTL-SDR symbol-rate limits. Specify the actual Pluto model and network configuration tested.
4. **Airspy Mini claims conflict within the release documentation.** The website grouped R2/Mini at 10 MS/s with full-band reception. The bundled README says Mini offers 6/3 MS/s and is too slow for the application's 9 MS/s requirement; VALIDATION.md reports only a fake-driver Mini fallback test. The public table now lists R2 separately and flags Mini support as unconfirmed. Determine actual support from the matching source and hardware tests.
5. **Driver instructions need a release-specific check.** Confirm Airspy/HackRF/RTL-SDR setup and document any required LimeSDR Mini and Pluto drivers. Current upstream OnAir documents a separate FT60x driver for LimeSDR Mini, but the fork's requirements cannot be inferred from the latest upstream alone. Reference: [OnAir installation instructions](https://github.com/adswill/OnAir#install).
6. **Application behaviour remains unverified.** Confirm version 0.1.0-beta.1, four-channel support, automatic browser launch, port 8090, automatic throughput measurement, calibration storage and the UI labels against the released build.
7. **Attribution needs the actual source revision.** Verify the OnAir commit used, its licence grant and the precise division of upstream and fork contributions. The current upstream repository cannot establish the contents of this binary release.

## Validation

All seven locally referenced images and both linked local text files exist. git diff --check passes. LICENSE was left unchanged. The ZIP integrity check passed and its SHA-256 matches the published checksum:

`ed05a6ba7e2a119a40ef052be3be28833d3cd3924d52f14ea7f1f5806d83df02`

The Windows executable was not run on this macOS host.

## Additional findings from the published archive

- **Bundled launch instructions do not work for the delivered package.** Its README tells users to run bash run-multi.sh from an MSYS2 project folder. No shell or Python scripts are included. The supplied CMD launcher changes to its own directory and runs SDR-Tiouner.exe. Replace the bundled launch section when building the next package.
- **RTL-SDR channel count conflicts.** Published release notes say “one channel”; the repository README previously said a second or third could work inside the captured window. The local README now flags additional channels as unconfirmed rather than choosing an unsupported claim.
- **Bundled architecture text may be stale.** It describes a fixed 745 MHz capture centre, whereas the repository README describes movable receive windows. Verify against the matching source before changing behaviour descriptions.
- **Validation is limited.** VALIDATION.md reports synthetic two-carrier tests and a short real-Airspy capture/throughput test without an RF source. It explicitly leaves live QO-100 decoding, live resource/latency measurements and a one-hour soak outstanding. This does not establish that no later testing occurred, but such evidence is not in this package.
- **Validation evidence is not bundled.** Referenced build-windows JSON measurements, screenshots, native test source and test scripts are absent. The document reports results but the archive cannot reproduce them alone.
- **No application source asset is listed.** The release has the binary ZIP and its checksum. GitHub-generated repository source archives would contain this documentation repository, not the modified receiver source.

Evidence: [published v0.1.0-beta.1 release](https://github.com/HB9IIU/SDR-Tiouner-releases/releases/tag/v0.1.0-beta.1), its README.md, VALIDATION.md, launcher and licence files. Published assets and release notes have not been modified; corrections so far are local repository edits.

