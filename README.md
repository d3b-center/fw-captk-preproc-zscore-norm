# CaPTk Preprocessing z-score normalization

Flywheel gear that implements the command line utility from CaPTk Preprocessing

## Notes

For ease of development I used the existing CaPTk Docker image, though there are issues with the available images:

- `cbica/captk:2021.03.29` was published 2 years ago (as of 11/21/2022) and has bugs with some of the flags in `Preprocessing -reg` . there were also issues with installing `jq` with `apt-get` on the OS (as defined in the Dockerfile)
- `cbica/captk:190rc` uses CentOS and with `Preprocess -reg` it throws an error `flag -rI not recognized` even though this option was not defined, for now I'm assuming it's an bug in how the program calls `greedy`
- `alexandergetka/captkdocker:06032022` is technically the most recent but has the same issue as 190rc

For now I'm using cbica/captk:2021.03.29 and removed the use of `jq` to parse the input flags in the `config.json` file. This at least gets the basic functionality of the registration to work, however it prevents me from implementing some additional flags: metrics_type, moving_segmentation, jacobian
