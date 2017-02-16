# Release Process

We have a goal of simultaneously serving multiple versions of the docs. This
means that there are multiple versions of the docs existing next to each other 
in the docs repo. This differs from what is normal, where only a single version
exists in the repo at a time and a git tag is created to reference old versions.

The versions that exist together are major or minor versions (e.g. v1.1, v1.2 
and v2.0). There only exists a single patch version (or pre-release
alphas, betas and release candidates) for each major/minor version. When
we do a new patch release, the updates are made in-place.


## Preparing for a release

1. Ensure master docs are passing semaphore tests.

2. Check out latest master locally.

## Creating the release

### When doing a major/minor release ONLY

These steps are for creating a new major/minor release, with the expectation that a release candidate will be created, published and tested before the final release is announced.

1. Run release-scripts/do_release.py to copy master directory to the new version directory
2. Fix calico-cni binary links which are not updated by the release script (see [#147](https://github.com/projectcalico/calico/issues/147)).
To locate all offending CNI links, run the following:
   ```
   grep -r calico-cni\/releases vX.Y
   ```

3. Add the new version to `_data/versions.yaml`
4. Add a section in `_config.yaml` so that `page.version` will be set correctly in the new subdirectory:

   ```
   -
     scope:
       path: vX.Y
     values:
       version: vX.Y
   ```

5. Test the changes locally then open a pull request, make sure it passes CI, then merge.

### Promoting a release candidate to a final release
1. Add a new `<option>` entry to the `<span class="dropdown">` in `_layouts/docwithnav.html` file. This step should NOT be performed until testing of the release is complete.

2. Modify the redirect in `/index.html` to point to your new release.. 
 
3. Test the changes locally then open a pull request, make sure it passes CI, then merge.

### Performing a "patch" release
Patch releases shouldn't include any new functionality, just bug fixes (expect during pre-release testing).

1. Add the new version to `_data/versions.yaml`
2. Test the changes locally then open a pull request, make sure it passes CI, then merge.
