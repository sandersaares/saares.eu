---
title: "Closing in on a common media application format"
date: 2016-06-16
categories: ["media streaming", "standards"]
description: "Apple begins adopting media streaming industry standards."
---

Apple announced today the [support for fragmented MP4 segments in HTTP Live Streaming (HLS)](https://developer.apple.com/videos/play/wwdc2016/504/), taking the first step in bringing together the two competing adaptive streaming universes that exist today: HLS and DASH. The former is the premier media delivery technology on Apple products while the latter is implemented on all other modern platforms.

There are two main differences between the two, which has meant that creating two different variants of every piece of content has been unavoidable in order to serve both Apple and non-Apple players. The key aspects are:

1. The media segment format – which until today had been MPEG-TS for HLS and MP4 for DASH[^1].
1. The encryption scheme – AES-CBC for HLS and AES-CTR for DASH.

Today's move by Apple eliminates the first difference, enabling the same segment format to be used for both DASH and HLS content. To present content without encryption in both adaptive streaming universes can now be accomplished by simply generating two kinds of manifest files for the exact same media segment files! This provides great savings in disk space, media processing complexity and delivery architecture.

What still remains is the obstacle of differing encryption formats. While both HLS-with-MP4 and DASH use Common Encryption, this is merely an umbrella term for multiple different and incompatible encryption schemes. The day when encrypted content can be shared between HLS and DASH remains in the future.

[^1]: While Apple contributed to DASH in its early days, this ended up merely leading to the creation of two “flavors” of DASH – one of which was very Apple-specific and not used by anyone for anything much. When people today speak of DASH they speak of the other, MP4-based variant of DASH.