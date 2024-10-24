# imagemin-mozjpeg

> [Imagemin](https://github.com/imagemin/imagemin) plugin for [mozjpeg](https://github.com/mozilla/mozjpeg)

## Install

```bash
$ npm install imagemin-mozjpeg
```

## Usage

```javascript
import imagemin from 'imagemin';
import imageminMozjpeg from 'imagemin-mozjpeg';

(async () => {
    await imagemin(['images/*.jpg'], {
        destination: 'build/images',
        plugins: [
            imageminMozjpeg()
        ]
    });

    console.log('Images optimized');
})();
```

## API

### imageminMozjpeg(options?)(buffer)

Returns a `Promise<Buffer>`.

#### options

- **Type:** `object`

##### quality

- **Type:** `number`
- **Description:** Compression quality, in range `0` (worst) to `100` (perfect).

##### progressive

- **Type:** `boolean`
- **Default:** `true`
- **Description:** `false` creates baseline JPEG file.

##### targa

- **Type:** `boolean`
- **Default:** `false`
- **Description:** Input file is Targa format (usually not needed).

##### revert

- **Type:** `boolean`
- **Default:** `false`
- **Description:** Revert to standard defaults instead of mozjpeg defaults.

##### fastCrush

- **Type:** `boolean`
- **Default:** `false`
- **Description:** Disable progressive scan optimization.

##### dcScanOpt

- **Type:** `number`
- **Default:** `1`
- **Description:** Set DC scan optimization mode.
  - `0`: One scan for all components
  - `1`: One scan per component
  - `2`: Optimize between one scan for all components and one scan for 1st component plus one scan for remaining components

##### trellis

- **Type:** `boolean`
- **Default:** `true`
- **Description:** [Trellis optimization](https://en.wikipedia.org/wiki/Trellis_quantization).

##### trellisDC

- **Type:** `boolean`
- **Default:** `true`
- **Description:** Trellis optimization of DC coefficients.

##### tune

- **Type:** `string`
- **Default:** `hvs-psnr`
- **Description:** Set Trellis optimization method. Available methods: `psnr`, `hvs-psnr`, `ssim`, `ms-ssim`.

##### overshoot

- **Type:** `boolean`
- **Default:** `true`
- **Description:** Black-on-white deringing via overshoot.

##### arithmetic

- **Type:** `boolean`
- **Default:** `false`
- **Description:** Use [arithmetic coding](https://en.wikipedia.org/wiki/Arithmetic_coding).

##### dct

- **Type:** `string`
- **Default:** `int`
- **Description:** Set [DCT](https://en.wikipedia.org/wiki/Discrete_cosine_transform) method:
  - `int`: Use integer DCT
  - `fast`: Use fast integer DCT (less accurate)
  - `float`: Use floating-point DCT

##### quantBaseline

- **Type:** `boolean`
- **Default:** `false`
- **Description:** Use 8-bit quantization table entries for baseline JPEG compatibility.

##### quantTable

- **Type:** `number`
- **Description:** Use predefined quantization table.
  - `0`: JPEG Annex K
  - `1`: Flat
  - `2`: Custom, tuned for MS-SSIM
  - `3`: ImageMagick table by N. Robidoux
  - `4`: Custom, tuned for PSNR-HVS
  - `5`: Table from paper by Klein, Silverstein, and Carney

##### smooth

- **Type:** `number`
- **Description:** Set the strength of smooth dithered input. (1...100)

##### maxMemory

- **Type:** `number`
- **Description:** Set the maximum memory to use in kilobytes.

##### sample

- **Type:** `string[]`
- **Description:** Set component sampling factors. Each item should be in the format `HxV`, for example `2x1`.

#### buffer

- **Type:** `buffer`
- **Description:** Buffer to optimize.
