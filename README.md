# docker-hashicorp-consul-template
A busybox:glibc based Docker container running HashiCorp's consul-template on CoreOS instances.

## From cloud-config
```
#cloud-config

coreos:
  units:
    - name: consul-template.service
      command: start
      content: |
        [Unit]
        Description=HashiCorp consul-template service
        Documentation=Rhttps://github.com/hashicorp/consul-template/blob/master/README.md
        [Service]
        Restart=always
        ExecStart=/usr/bin/docker run --rm --name consul-template \
          --net=host \
          godmodelabs/hashicorp-consul-template
        ExecStop=-/usr/bin/docker stop consul-template
```
