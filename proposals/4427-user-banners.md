# MSC4427: Custom banners for user profiles

On many platforms, users have additional customization options for 
their profile, including but not limited to banners.

Banners are displayed above, and often slightly behind a users' avatar,
most commonly featuring landscape content.

This MSC aims to standardize these banners across the matrix ecosystem.

## Proposal

Banners are something that is already widely represented on instant
messaging platforms, and even in some UI designs in the Matrix
ecosystem. Yet, there isn't a standardized field (outside of 
non-specced implementations in some clients) to read banners from.

We add a new field to represent banners:
```json
{
  "avatar_url": "mxc://matrix.org/SDGdghriugerRg",
  "banner_url": "mxc://matrix.org/example123",
  "displayname": "Alice Margatroid",
  "m.example_field": "custom_value",
  "m.tz": "Europe/London"
}
```

Clients can then use this field to load user banners.

## Potential issues

Some clients, like [extera](https://matrix.org/ecosystem/clients/extera-next/)
already had user banners in the past. This field may not be read by
those clients and users which wish to keep their banners once this is
implemented will have to reupload their banner.

## Security considerations

The same security precautions apply here as they do for avatars. Uploaded 
banners should always be some kind of image data (i.e image/* mime-type)
and never other arbitrary files.

## Alternatives

This field could also be implemented as `m.banner_url`, as per MSC4133.

## Unstable prefix

This MSC is a non-breaking change, and as such `banner_url` can be used as-is
even before this MSC is merged.

## Dependencies

None
