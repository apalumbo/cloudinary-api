---
title: Options
description: 'Configuration options for Cloudinary url builder'
position: 3
category: Guide
---

To configure the builder globally, you can use `setConfig()` method:

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  cloudName: 'your-cloud-name',
})
```

To configure the builder per url generation call, you can use `cloud` field of `options` parameter of that call.

```js
import { buildImageUrl } from 'cloudinary-builder-url'

const src = buildImageUrl('public-id', {
  cloud: {
    cloudName: 'your-cloud-name',
  }
})
```

## Cloudinary options

### `cloudName`

* Type: `String`
* **Required**

The cloud name associated with your Cloudinary account. It is used to configure and enable Cloudinary features such as generating delivery asset URL. 

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  cloudName: 'your-cloud-name',
})
```

Cloud name presents in every delivered URL from Cloudinary, hence it's important to have it configured correctly.

<alert type="info">

You can find your cloud name details in **Dashboard** page, or in **Account Settings** page in [Cloudinary console](https://cloudinary.com/console)

</alert>

### `secure`

* Type: `Boolean`
* Default: `true`

Force secure HTTPS delivery urls for all assets (images + videos) generated by Cloudinary, even if they are embedded in HTTP originally.

Disable this flag to have all delivery urls built with HTTP protocol instead.

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  secure: false
})
```

### `secureDistribution`

* Type: `String`
* Relevant only when `secure` is `true`

Set custom domain name for building **secure HTTPS** urls.

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  secureDistribution: 'your-custome-domain-name'
})
```

<alert type="info">

Only relevant if you are Advanced plan Cloudinary user with private CDN distribution and custom CNAME set. You can see [more details here](https://cloudinary.com/documentation/advanced_url_delivery_options#private_cdns_and_cnames)

</alert>

### `cname`

* Type: `String`
* Use only when `secure` is `false`

Set custom domain name for building **non-secure HTTP** urls.

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  cname: 'your-custome-domain-name'
})
```

<alert type="info">

Only relevant if you are Advanced plan Cloudinary user with private CDN distribution and custom CNAME set. You can see [more details here](https://cloudinary.com/documentation/advanced_url_delivery_options#private_cdns_and_cnames)

</alert>

### `privateCdn`

* Type: `Boolean`
* Default: `false`

Set to `true` if you'd like to use private CDN distribution.

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  privateCDN: true
})
```

<alert type="info">

Only relevant for Advanced plan Cloudinary users. You can see [more details here](https://cloudinary.com/documentation/advanced_url_delivery_options#private_cdns_and_cnames)

</alert>

## Asset options

Below are the configuration options to apply to assets specifically (images and videos).

### `storageType`

* Type: `String`
* Default: `upload`
* Accepted values: `upload` | `fetch` | `private` | `authenticated`| `sprite` |`facebook` | `twitter` | `youtube` | `vimeo`

The storage and delivery type of asset in Cloudinary. 

```js
import { setConfig, STORAGE_TYPES } from 'cloudinary-builder-url'

setConfig({
  storageType: STORAGE_TYPES.UPLOAD //upload
})
```

<alert type="info">

`STORAGE_TYPES` contains all the valid storage types.

</alert>

### `resourceType`

* Type: `String`
* Default: `image`
* Accepted values: `image` | `video` | `raw`

Type of the asset(s)

```js
import { setConfig, RESOURCE_TYPES } from 'cloudinary-builder-url'

setConfig({
  storageType: RESOURCE_TYPES.IMAGE //image
})
```

<alert type="info">

`RESOURCE_TYPES` contains all the valid resources types.

</alert>

### `version`

* Type: `Number` | `String`
* Default: `1`

The timestamp of uploaded asset. If there is no version indicated, a previously cache version of asset will be served instead.

It's **only relevant** to uploaded asset to Cloudinary.

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  version: 1312461204
})
```

<alert type="info">

To use `version`, you need to have `forceVersion` enabled.

</alert>

### `forceVersion`

* Type: `Boolean`
* Default: `false`

To enable applying version on asset whenever possible. It's **only relevant** to uploaded asset to Cloudinary.

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  forceVersion: true
})
```

### `signature`

* Type: `String`

A string includes all the components of the delivery URL that will come after the signature component.

```js
import { setConfig } from 'cloudinary-builder-url'

setConfig({
  signature: 'my-signature'
})
```

See [Signature Documentation](https://cloudinary.com/documentation/signatures) for more details.