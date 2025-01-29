![Screenshot_20240312_002014_com android gallery3 2](https://github.com/user-attachments/assets/4b5699c7-d9d0-44c9-b828-89169dd8ac19)
![Screenshot_20240312_002014_com android gallery3](https://github.com/user-attachments/assets/a0f4a5eb-fa6f-488b-9377-74809dd92e11)
![2024-06-14 19 04 57](https://github.com/user-attachments/assets/ea160cf7-9f88-4354-9e9e-2e5b53261bf2)
![20200427_214002000_iOS](https://github.com/user-attachments/assets/e94e29d7-be17-43ec-93e2-0ac08ba4210c)
![document-open-recent](https://github.com/user-attachments/assets/227a07b2-5c9f-4f52-80e9-581c11966f66)
![entry-restore](https://github.com/user-attachments/assets/290dfe13-ec8b-47c5-80d2-527650fd8c67)
# Feature-based versioning

Feature-based versioning allows us to define and control the versions of an arbitrarily named "feature" in one place.

**Note**: Do not delete `data/features/placeholder.yml` because it is used by tests.

## How it works

Add a new YAML file with the feature name you want to use in this directory. For a feature named `meow`, that would be `data/features/meow.yml`.

Add a `versions` block to the YML file with the short names of the versions the feature is available in. For example:

```yaml
versions:
  fpt: '*'
  ghec: '*'
  ghes: '>3.1'
```

The format and allowed values are the same as the [frontmatter versions property](/content#versions).

### Liquid conditionals

Now you can use `{% ifversion meow %} ... {% endif %}` in content files!

### Frontmatter

You can also use the feature in frontmatter in content files:

```yaml
versions:
  fpt: '*'
  ghec: '*'
  ghes: '>3.1'
  feature: 'meow'
```

You cannot use `feature:` to specify multiple concurrent versions, as this is not supported. Alternatively, you could create a new feature-based versioning file with the required versioning.

## Schema enforcement

The schema for validating the feature versioning lives in [`src/data-directory/lib/data-schemas/features.js`](../../src/data-directory/lib/data-schemas/features.js).

## Script to remove feature tags

TBD!
