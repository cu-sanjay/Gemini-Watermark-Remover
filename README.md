<p align="center">
  <img src="docs/Remover.png" width="200" alt="Gemini Watermark Remover Logo">
</p>

<div align="center">

# Gemini Watermark Remover

### Advanced privacy-first browser extension for automatically removing Google Gemini AI image watermarks.

<br>

<a href="https://microsoftedge.microsoft.com/addons/detail/nlfhgjjionkpldaikdlhmjhhpkjnpmle">
  <img src="https://github.com/user-attachments/assets/e7144ef4-82cc-460e-b3ea-b1eeb3f8f196" alt="Microsoft Edge Add-ons Badge" width="260">
</a>

</div>

## Overview

Gemini Watermark Remover is designed for users who regularly work with AI-generated images from Google Gemini.  
The extension automatically removes embedded Gemini watermarks before the image is downloaded, producing clean output images without quality loss or additional editing tools.

The extension works silently in the background and activates only on the Gemini website.  
There are no buttons, no setup screens, and no manual interaction required.

Tested and verified on both **Google Chrome** and **Microsoft Edge**.

## How It Works (Reverse Alpha Blending)

Gemini applies its watermark using alpha blending. This extension mathematically reverses the process to reconstruct the original pixel data.

Watermarked pixel model:

$$
C_{watermarked} = \alpha \cdot C_{logo} + (1 - \alpha) \cdot C_{original}
$$

Recovered pixel calculation:

$$
C_{original} = \frac{C_{watermarked} - \alpha \cdot C_{logo}}{1 - \alpha}
$$

Where:

- $C_{original}$ is the restored pixel value  
- $C_{watermarked}$ is the visible pixel value  
- $\alpha$ is the transparency mask derived from watermark samples  
- $C_{logo}$ is the fixed watermark color value ($255$)

The extension uses precomputed watermark templates for both Gemini watermark variants.

## Features

- Fully automatic watermark removal
- Works with the default Gemini download button
- No visible artifacts or quality degradation
- 100% local browser-side processing
- No tracking or analytics
- Lightweight and performance optimized
- Compatible with Manifest V3
- Clean and minimal workflow

# Before and After Examples

<table align="center">
<tr>
<td align="center">
<b>Before (With Watermark)</b><br><br>
<img src="docs/Gemini_Generated_Image_4w7qn64w7qn64w7q_original.png" width="360">
</td>

<td align="center">
<b>After (Watermark Removed)</b><br><br>
<img src="docs/Gemini_Generated_Image_4w7qn64w7qn64w7q.png" width="360">
</td>
</tr>

<tr>
<td align="center">
<img src="https://github.com/user-attachments/assets/73b908f5-ebce-4f3f-8984-5b7924d1917f" width="360">
</td>

<td align="center">
<img src="https://github.com/user-attachments/assets/5a1a424e-204a-424f-b521-d1ce20532b61" width="360">
</td>
</tr>

<tr>
<td align="center">
<img src="https://github.com/user-attachments/assets/b2c1f734-89bc-453d-a090-65c3829cd834" width="360">
</td>

<td align="center">
<img src="https://github.com/user-attachments/assets/cd0b6d42-72fc-4ea4-96c8-75f9f010a343" width="360">
</td>
</tr>

<tr>
<td align="center">
<img src="https://github.com/user-attachments/assets/ff801d9f-9c9d-4114-9c6d-ad6c93b45e66" width="360">
</td>

<td align="center">
<img src="https://github.com/user-attachments/assets/634ae313-80f9-4eea-aaba-51eb2e01e892" width="360">
</td>
</tr>

</table>

## Installation

### Microsoft Edge (Recommended)

Install directly from the Microsoft Edge Add-ons Store using the badge above.

### Google Chrome (CRX Installation)

A packaged CRX build is available in the releases section.

1. Download the `.crx` file from Releases  
2. Open:

   ```
   chrome://extensions
   ```

3. Enable **Developer Mode**  
4. Drag and drop the `.crx` file into the extensions page  
5. Confirm installation

>[!WARNING]
> If Chrome blocks CRX installation, use the manual installation method below.

### Manual Installation (Chrome and Edge)

1. Download and extract the source code  
2. Open:
   - `chrome://extensions`
   - `edge://extensions`
3. Enable **Developer Mode**
4. Click **Load unpacked**
5. Select the extracted project folder

The extension activates automatically on the Gemini website.

## Usage

1. Open the Gemini AI website  
2. Generate or view images normally  
3. Click the default download button  
4. The downloaded image will automatically have the watermark removed

No additional steps are required.

## Development

To modify or rebuild the extension:

1. Edit:

   ```
   src/content.template.js
   ```

2. Run:

   ```bash
   node build.js
   ```

This regenerates the final content script using updated watermark templates and processing logic.

## Privacy

- No personal data collected  
- No image uploads  
- No external requests  
- Everything runs fully locally on your device
