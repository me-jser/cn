# 5. 数据安全

京东云遵循数据安全生命周期管理的业界先进标准，采取管理和技术两方面的手段进行全面数据安全体系建设。在身份认证、权限管理、访问控制、数据加密、数据隔离、传输安全、存储安全、数据销毁等方面，保证用户对其数据的隐私权、所有权和控制权不受侵犯，为用户提供最切实有效的数据保护。

· 身份认证和访问控制

京东云提供的一项用户身份管理与资源访问控制服务（IAM）。用户可以通过 IAM 服务创建、管理子用户账号，并控制这些子用户访问京东云资源的权限。详情请见 “访问控制” 章节。

· 静态数据保护

用户负责确保按标准加密云平台中存储的数据。云平台提供各种加密功能，便于用户选择满足自己需求的最佳解决方案。帮助用户保持对密钥的控制，以便云应用程序和服务用于加密数据，使用云磁盘加密来加密虚拟机，存储服务加密可以加密用户存储帐户中的所有数据。提供各种数据存储解决方案，以满足不同需求，包括文件、磁盘和表存储等。

· 数据隔离

对云端数据的隔离是通过私有网络 (VPC)实施的，此私有网络空间由用户完全掌控，它将不同租户间的网络深度隔离，保证了不同租户间的数据不会被越权获取。详情请见 “ 私有网络” 章节。

· 传输中数据保护

云产品控制台上的通信都受到了 HTTPS 安全协议的加密保护。使用行业标准传输层安全性的 SSL/TLS
加密在用户与云、云平台系统和数据中心之间的内部通信，保护传入或传出组件的数据，以及在内部传输的数据。

· 数据冗余

出现网络攻击或者数据中心遭到物理损坏时，可确保数据受到保护。数据可在选定的地理区域中进行复制以实现冗余，但不会传输到此区域以外。用户可以使用多个选项来复制数据，包括指定副本数量，以及复制数据中心的数量和位置。

· 数据销毁

在用户提出请求和合同终止时，京东云会执行完全数据删除。当用户删除数据或离开京东云时，将根据行业标准实践对所有退役的磁性存储设备进行消磁和物理销毁。当某个存储设备已达到其使用寿命的最后时期时，京东云程序中包括的退役流程可防止用户数据暴露给未授权的个人。
