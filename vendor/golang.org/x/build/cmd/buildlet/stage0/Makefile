#
# The stage0 binaries are typically baked into VM images and container
# images and are NOT downloaded per build or VM/container start-up.
# The only reason we upload them to GCS is because that's where the
# automated VM/container creation scripts download them from.
#
# The notable exception is our Mac VMs on MacStadium. In those cases,
# the images actually do download the stage0 binary on start-up.
#

usage: FORCE
	# See targets in Makefile
	exit 1

FORCE:

buildlet-stage0.windows-amd64: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

buildlet-stage0.linux-arm-scaleway: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

buildlet-stage0.linux-arm64: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

buildlet-stage0.linux-ppc64: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

buildlet-stage0.linux-ppc64le: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

buildlet-stage0.solaris-amd64: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

# No staging vs prod targets here, because this file gets baked into
# the Docker layers on gcr.io (which do have staging vs prod names).
# That is, this file on GCS is only used at "docker build"-time, not
# during day-to-day builds.
buildlet-stage0.linux-amd64-kube: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

buildlet-stage0.linux-amd64-static: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false --static go-builder-data/$@

buildlet-stage0.linux-s390x: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=$@ --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false go-builder-data/$@

# macstadium uploads all the darwin-amd64 stage0 binary as three
# different filenames, which is used by four different Mac VM images.
# See the env/darwin/macstadium/** files for details.
macstadium: run-builder-darwin-10_8.gz run-builder-darwin-10_10.gz run-builder-darwin-10_11.gz

run-builder-darwin-10_8.gz: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=darwin-amd64 --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false --gzip go-builder-data/$@

run-builder-darwin-10_10.gz: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=darwin-amd64 --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false --gzip go-builder-data/$@

# run-builder-darwin-10_11.gz is used by both our macOS 10.11 and 10.12 VM images.
run-builder-darwin-10_11.gz: FORCE
	go install golang.org/x/build/cmd/upload
	upload --verbose --osarch=darwin-amd64 --file=go:golang.org/x/build/cmd/buildlet/stage0 --public --cacheable=false --gzip go-builder-data/$@
