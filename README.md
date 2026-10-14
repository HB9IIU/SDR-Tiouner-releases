<p align="center"><img src="images/sdr-tiouner-banner.png" alt="SDR-Tiouner - multi channel QO-100 DATV" width="640"></p>

<h2 align="center">DEMO</h2>

<p align="center">
  <a href="https://youtu.be/zrdZYKuxhsY" title="Watch the SDR-Tiouner demo on YouTube">
    <img src="https://img.youtube.com/vi/zrdZYKuxhsY/maxresdefault.jpg" alt="SDR-Tiouner demo video (click to watch on YouTube)" width="640">
  </a>
  <br>
  <sub>Click the picture to watch the demo on YouTube</sub>
</p>

# SDR-Tiouner

**Multi-channel QO-100 DATV receiver, by HB9IIU.** Up to four narrowband DATV channels from one wideband SDR, in your web browser.

> **Beta.** This is a first public beta (`0.1.0-beta.1`). It works, but expect rough edges. Please report what you find.

Free of charge, not for sale. If anyone asks you to pay for it, please do not, and tell me.

## Download

Get **`SDR-Tiouner-windows-x64.zip`** from the [Releases](../../releases) page. Unzip it anywhere and run `SDR-Tiouner.exe`
(or `Start SDR-Tiouner.cmd`). There is no installer. The page opens in your browser at <http://127.0.0.1:8090>.

## What you need

- Windows 10 or 11, 64-bit, a processor with AVX2 (anything from about 2014 on)
- A modern browser (Chrome, Edge, Firefox)
- One of these radios, and a QO-100 narrowband receive chain (LNB at 9750 MHz, IF about 740 MHz):

| | Radio | What you get |
|---|---|---|
| <img src="images/airspy-r2.jpg" width="150" alt="Airspy R2"> | **Airspy R2 / Mini** | Full band, 10 Msps |
| <img src="images/sdrplay-rsp2.png" width="150" alt="SDRplay RSP2"> | **SDRplay** RSP1 / RSP2 / RSPdx / RSPduo | Full band. Needs the free [SDRplay API](https://www.sdrplay.com/api/) installed once |
| <img src="images/hackrf-one.jpg" width="150" alt="HackRF One"> | **HackRF One** | Full band |
| <img src="images/limesdr-mini.jpg" width="150" alt="LimeSDR Mini"> | **LimeSDR Mini** | Full band on **USB 3**. On USB 2 only about 3.5 MHz of the band at once |
| <img src="images/adalm-pluto.jpg" width="150" alt="ADALM-Pluto"> | **PlutoSDR** | USB: about 6 MHz of the band at once. Gigabit network: full band. Found on USB or on your network |
| <img src="images/rtl-sdr-v4.jpg" width="150" alt="RTL-SDR"> | **RTL-SDR** | A window of about 2.4 MHz: it starts with one channel, and a second or third works when it falls inside that window. Narrow channels only (up to about 1 MS/s) |

<sub>Photos: HB9IIU.</sub>

If a radio's connection cannot carry the full band, SDR-Tiouner measures it, runs at what the link allows, and tells you.

## First use

1. Plug in the radio, start the program, open the page.
2. Select your radio and press **Start capture**.
3. Press **Calibrate** once per radio (needs the QO-100 beacon at 10491.500 MHz). The correction is stored per radio.
4. Drag the channel tabs onto the signals, or click a signal in the BATC spectrum.

The three buttons above the spectrum move the receive window left, centre or right in the band.

## One-time driver step (some radios)

Windows has to attach a USB driver to HackRF, Airspy and RTL-SDR on a PC that has never used them: run [Zadig](https://zadig.akeo.ie)
once and install **WinUSB** for the radio. The program tells you if that is what is missing.

## Licence and source code

SDR-Tiouner is free software under the **GNU GPL v3 or later** and is based on [OnAir](https://github.com/adswill/OnAir).
This page carries the program only. **The complete source code is available on request, free of charge**: see
[`SOURCE-OFFER.txt`](SOURCE-OFFER.txt) and write to the contact given there. The release also contains the licences and
notices of every third-party component (`THIRD-PARTY-NOTICES.txt`, `licenses/`).

73 and good DX,
HB9IIU
