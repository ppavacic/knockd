# knockd-iptables

## Usage

```bash
docker run --net=host --privileged --name knockd -d ppavacic/knockd SEQUENCE PORT INTERFACE
```

If INTERFACE is empty, will listen to all available interfaces.

## Example

```bash
docker run --net=host --privileged --name knockd -d ppavacic/knockd 7000,8000,9000 22,33,44 eth0
```

## Contribute

https://github.com/ppavacic/knockd/