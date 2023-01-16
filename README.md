# Paketo Buildpacks - ARM64

The builder image provided by Paketo Buildpacks doesn't currently support ARM64 architectures.
Instead, you can use [ghcr.io/thomasvitale/java-builder-arm64](https://github.com/users/ThomasVitale/packages/container/package/java-builder-arm64) based on the [work](https://dashaun.com/posts/teamwork-makes-the-dream-work-for-multiarch-builder/) done by Dashaun Carter.

In a Spring Boot project, you can configure Buildpacks in your `build.gradle` file as follows:

```shell
tasks.named('bootBuildImage') {
	if (System.getProperty( "os.arch" ).toLowerCase().startsWith('aarch')) {
		builder = "ghcr.io/thomasvitale/java-builder-arm64"
	}
  builder = "paketobuildpacks/builder:tiny"
}
```
