# parallel-install-snap-test
A simple test case to test parallel installs of snaps

To test this:
1. Set the version to 0.1 in the snapcraft.yaml
2. Build the snap with `$snapcraft`. See that `parallel-install-test_0.1_amd64.snap` is created.
3. Set the version to 0.2 in the snapcraft.yaml
4. Build the second snap with `$snapcraft`. See that `parallel-install-test_0.2_amd64.snap` is created.
5. Install the first snap with `sudo snap install parallel-install-test_0.1_amd64.snap --dangerous`
6. Install the second snap in parallel with `sudo snap install --name parallel-install-test_2 parallel-install-test_0.2_amd64.snap --dangerous`

If there were an issue of just having multiple apps in the `snapcraft.yaml`, then the second snap install should fail similar to the [firefox parallel install failure](https://bugzilla.mozilla.org/show_bug.cgi?id=1825103).
