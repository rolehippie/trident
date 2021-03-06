# trident

[![Source Code](https://img.shields.io/badge/github-source%20code-blue?logo=github&logoColor=white)](https://github.com/rolehippie/trident) [![Build Status](https://img.shields.io/drone/build/rolehippie/trident/master?logo=drone)](https://cloud.drone.io/rolehippie/trident) [![License: Apache-2.0](https://img.shields.io/github/license/rolehippie/trident)](https://github.com/rolehippie/trident/blob/master/LICENSE) 

Ansible role to install and configure Trident on Kubernetes. 

## Sponsor 

[![Proact Deutschland GmbH](https://proact.eu/wp-content/uploads/2020/03/proact-logo.png)](https://proact.eu) 

Building and improving this Ansible role have been sponsored by my employer **Proact Deutschland GmbH**.

## Table of content

* [Default Variables](#default-variables)
  * [trident_backends](#trident_backends)
  * [trident_classes](#trident_classes)
  * [trident_download](#trident_download)
  * [trident_kubeconfig](#trident_kubeconfig)
  * [trident_namespace](#trident_namespace)
  * [trident_version](#trident_version)
* [Dependencies](#dependencies)
* [License](#license)
* [Author](#author)

---

## Default Variables

### trident_backends

List of available backends

#### Default value

```YAML
trident_backends: []
```

#### Example usage

```YAML
trident_backends:
  - name: ssd
    config:
      version: 1
      storageDriverName: ontap-nas
      managementLIF: 10.20.0.2
      dataLIF: 10.30.0.2
      svm: svm_nfs
      username: username
      password: p455w0rd
```

### trident_classes

List of Kubernetes storage classes

#### Default value

```YAML
trident_classes: []
```

#### Example usage

```YAML
trident_classes:
  - name: ssd
    default: True
    backend: ontap-nas
    filesystem: ext4
```

### trident_download

URL to the archive of the release to install

#### Default value

```YAML
trident_download: https://github.com/NetApp/trident/releases/download/v{{ trident_version
  }}/trident-installer-{{ trident_version }}.tar.gz
```

### trident_kubeconfig

Path to a valid kubeconfig file

#### Default value

```YAML
trident_kubeconfig: /etc/kubernetes/admin.conf
```

### trident_namespace

Namespace used within Kubernetes

#### Default value

```YAML
trident_namespace: trident-system
```

### trident_version

Version of the Trident release to install

#### Default value

```YAML
trident_version: 20.10.1
```

## Dependencies

* None

## License

Apache-2.0

## Author

[Thomas Boerger](https://github.com/tboerger)
