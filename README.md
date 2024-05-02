# Image-Matching-Models

To use this simply run

```
git clone --recursive https://github.com/gmberton/EarthMatch
```

NOTE THE `--recursive` !!!

Then run this script, which will perform inference on the 3 folders of image pairs inside `./assets`. It is possible to specify also resolution and num_keypoints.

```
python run_matching.py -m sift-lg
```

Where `sift-lg` will use `SIFT + LightGlue`. You can choose any of the following methods:
loftr, sift-lg, superpoint-lg, disk-lg, aliked-lg, doghardnet-lg, roma, dedode, steerers, sift-nn, orb-nn, patch2pix, patch2pix_superglue, superglue, r2d2, d2net, duster, doghardnet-nn

The script will generate an image with the matching keypoints for each pair, under `./outputs` .


### Adding a new method

To add a new method simply add it to `./matching`. If the method requires external modules, you can add them to `./third_party` with `git submodule add`: for example, I've used this command to add the LightGlue module which is automatically downloaded when using `--recursive`

```
git submodule add https://github.com/cvg/LightGlue third_party/LightGlue
```

This command automatically modifies `.gitmodules` (and modifying it manually doesn't work).


## TODO list

1. It would be nice if we could import only the module that is actually used without making `matching/__init__.py` too ugly
2. Clean the README for release, add more examples in assets, we could use one example of outdoor buildings, one indoor, and one satellite
3. Remove method-specific hyperparams like dedode_thresh, lowethresh, steerer_type (or find a better way to use them?)

## Longer term TODO list

- [ ] It might be useful to return other params (e.g. `kpts0, kpts1`) for some methods
- [ ] Add DeDoDe + LightGlue from kornia
- [ ] Add CVNet
- [ ] Add TransVPR
- [ ] Add Patch-NetVLAD
- [ ] Add SelaVPR
