---
title: "Linux における .NET Core の前提条件"
description: "Linux マシンで .NET Core アプリケーションを開発、展開、および実行するために必要なサポートされている Linux のバージョンと .NET Core の依存関係。"
keywords: .NET, .NET Core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.translationtype: HT
ms.sourcegitcommit: 7bbb8405f39a52d2798fd1dbc78f3116cb3bedbb
ms.openlocfilehash: 9864ffa31caa007cb649a9e6e8913863d9cb2c35
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---

# <a name="prerequisites-for-net-core-on-linux"></a>Linux における .NET Core の前提条件

この記事では、Linux で .NET Core アプリケーションを開発するために必要な依存関係を示します。 後述のサポートされている Linux ディストリビューション/バージョンと依存関係は、Linux で .NET Core アプリを開発する次の 2 つの方法に適用されます。

* [好みのエディターでのコマンドライン](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>サポートされている Linux バージョン

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.0 は、1 つのオペレーティング システムとして Linux を扱います。 サポートされている Linux ディストリビューション用に、1 つの Linux ビルド (チップ アーキテクチャあたり) があります。

NET Core 2.x は、次の Linux x64 ディストリビューション/バージョンでサポートされています。

 * Red Hat Enterprise Linux 7
 * CentOS 7
 * Oracle Linux 7
 * Fedora 25、Fedora 26
 * Debian 8.7 以降のバージョン 
 * Ubuntu 17.04、Ubuntu 16.04、Ubuntu 14.04
 * Linux Mint 18、Linux Mint 17
 * openSUSE 42.2 以降のバージョン
 * SUSE Enterprise Linux (SLES) 12 SP2 以降のバージョン

.NET Core 2.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)」 (.NET Core 2.x がサポートされる OS のバージョン) を参照してください。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

.NET Core 1.x は、次の Linux x64 ディストリビューション/バージョンでサポートされています。

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 24
* Debian 8.2 以降のバージョン
* Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10\*
 * Ubuntu 16.10 は、.NET Core 1.1 の最新の修正プログラム リリースによってサポートされます
* Linux Mint 17
* openSUSE 42.1 以降のバージョン (.NET Core 1.1)

.NET Core 1.x がサポートされているオペレーティング システム (サポートされている OS バージョン以外) の完全なリスト、およびライフサイクル ポリシーのリンクについては、「[.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)」 (.NET Core 1.x がサポートされる OS のバージョン) を参照してください。

---

## <a name="linux-distribution-dependencies"></a>Linux ディストリビューションの依存関係

### <a name="ubuntu"></a>Ubuntu

Ubuntu ディストリビューションには、次のライブラリがインストールされている必要があります。

* libunwind8
* libunwind8-dev
* gettext
* libicu-dev
* liblttng-ust-dev
* libcurl4-openssl-dev
* libssl-dev
* uuid-dev
* unzip

### <a name="centos"></a>CentOS

CentOS ディストリビューションには、次のライブラリがインストールされている必要があります。

* deltarpm
* epel-release
* unzip
* libunwind
* gettext
* libcurl-devel
* openssl-devel
* zlib
* libicu-devel

依存関係の詳細については、「[Self-contained Linux applications (自己完結型 Linux アプリケーション)](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」をご覧ください。

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>ネイティブ インストーラーを使用した .NET Core の依存関係のインストール

.NET Core ネイティブ インストーラーは、サポートされている Linux ディストリビューション/バージョンに利用できます。 このネイティブ インストーラーは、サーバーへの admin (sudo) アクセスを必要とします。 ネイティブ インストーラーを使用することの利点は、.NET Core ネイティブの依存関係がすべてインストールされることです。 また、ネイティブ インストーラーでは、.NET Core SDK もシステム全体にインストールします。

Linux では、2 つのインストーラー パッケージから選択できます。

* フィードベースのパッケージ マネージャー (Ubuntu では apt-get、CentOS/RHEL では yum など) を使用する
* パッケージ自体 (DEB または RPM) を使用する

### <a name="scripting-installs-with-the-net-core-installer-script"></a>.NET Core インストーラー スクリプトを使用したスクリプトのインストール

`dotnet-install` スクリプトは、CLI ツールチェーンと共有ランタイムの非管理者インストールを実行するために使用されます。 スクリプトは [CLI GitHub リポジトリ](https://github.com/dotnet/cli/tree/rel/1.0.0/scripts/obtain)からダウンロードできます。

インストーラーの bash スクリプトは、自動化シナリオと管理者以外のインストールで使用されます。 このスクリプトは、PowerShell のスイッチも読み取るので、Linux/OS X システムのスクリプトで使うことができます。

> [!IMPORTANT]
> スクリプトを実行する前に、必要な[依存関係](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)をすべてインストールします。

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7 用の .NET Core をインストールする

RHEL 7 に .NET Core をインストールするには:

1. RHEL 7 サブスクリプションで利用できる Red Hat .NET チャネルを有効にします。
    * Red Hat Enterprise 7 Server の場合は、次を使用します。
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 Workstation の場合は、次を使用します。
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 HPC Compute Node の場合は、次を使用します。
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. scl ツールをインストールします。

    ```bash
    yum install scl-utils
    ```
    
3. .NET Core をインストールします。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET Core 2.0 SDK とランタイムをインストールします。

   ```bash
   yum install rh-dotnet20
   ```

環境に対して .NET Core 2.0 SDK/ランタイムを有効にします。

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.1**

.NET Core 1.1 SDK とランタイムをインストールします。

   ```bash
   yum install rh-dotnetcore11
   ```

環境に対して .NET Core 1.1 SDK/ランタイムを有効にします。

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

**.NET Core 1.0**

.NET Core 1.0 SDK とランタイムをインストールします。

   ```bash
   yum install rh-dotnetcore10
   ```

環境に対して .NET Core 1.0 SDK/ランタイムを有効にします。

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

     ```bash
     dotnet --version
     ```

Red Hat .NET チャネル アクセスの登録に関するヘルプについては、Red Hat の「[Chapter 1 of the .NET Core 1.1 Getting Started Guide](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/)」 (.NET Core 1.1 ファースト ステップ ガイドの第 1 章) を参照してください。

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a>.NET Core for Ubuntu 14.04、Ubuntu 16.04、Ubuntu 16.10 および Linux Mint 17、Linux Mint 18 (64 ビット)

1. システムから**以前のプレビュー** バージョンの .NET Core を削除します。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. 信頼済みとして Microsoft プロダクト キーを登録します。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. 必要なバージョンのホスト パッケージ フィードを設定します。

   **Ubuntu 17.04**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 16.04 / Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 14.04 / Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. .NET Core をインストールします。

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 必要なバージョンのホスト パッケージ フィードを設定します。

   **Ubuntu 16.10**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  **Ubuntu 16.04 / Linux Mint 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   **Ubuntu 14.04 / Linux Mint 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. Ubuntu または Linux Mint に、.NET Core 1.x をインストールします。

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a>Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールする

Debian 8 または Debian 9 (64 ビット) 用の .NET Core をインストールするには:

1. システムから**以前のプレビュー** バージョンの .NET Core を削除します。

> [!NOTE]
> tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. システムのコンポーネントをインストールします。

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. 信頼済みの Microsoft プロダクト キーを登録します。

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. Microsoft 製品フィードを登録します。

   **Debian 9 (Stretch)**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   **Debian 8 (Jessie)**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. .NET Core SDK バイナリを抽出します。

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. パスに dotnet を追加します。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 必須コンポーネントを取得します。

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. .NET Core SDK バイナリ (tarball) をダウンロードします。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. .NET Core SDK バイナリを抽出します。

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. パスに dotnet を追加します。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a>.NET Core for Fedora 24、Fedora 25、または Fedora 26 (64 ビット) をインストールする

.NET Core for Fedora 26、Fedora 25 (.NET Core 2.x)、または Fedora 24 (.NET Core 1.x) をインストールするには:

1. システムから**以前のプレビュー** バージョンの .NET Core を削除します。

> [!NOTE]
> tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Fedora 26 または Fedora 25**

2. Microsoft 署名キーを登録します。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. dotnet 製品フィードを追加します。

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. .NET Core SDK をインストールします。

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. パスに dotnet を追加します。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Fedora 24**

2. 必須コンポーネントを取得します。

   ```bash
   sudo dnf install libunwind libicu
   ```

3. .NET Core SDK バイナリ (tarball) をダウンロードします。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. .NET Core SDK バイナリを抽出します。

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. パスに dotnet を追加します。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>CentOS 7.1 (64 bit) および Oracle Linux 7.1 (64 bit) 用の .NET Core をインストールする

CentOS 7.1 (64 bit) および Oracle Linux 7.1 (64 bit) 用の .NET Core をインストールするには

1. システムから**以前のプレビュー** バージョンの .NET Core を削除します。

> [!NOTE]
> tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Microsoft 署名キーを登録します。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Microsoft 製品フィードを追加します。

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. .NET Core SDK をインストールします。

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. パスに dotnet を追加します。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 必須コンポーネントを取得します。

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. .NET Core SDK バイナリ (tarball) をダウンロードします。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. .NET Core SDK バイナリを抽出します。

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. パスに dotnet を追加します。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a>.NET Core for SUSE Linux Enterprise Server (64 ビット) をインストールする

.NET Core 2.x for SUSE Linux Enterprise Server (SLES) 12 SP2 (64 ビット) をインストールするには:

1. システムから**以前のプレビュー** バージョンの .NET Core を削除します。

2. dotnet 製品フィードを追加します。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. .NET Core SDK をインストールします。

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. パスに dotnet を追加します。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a>.NET Core for openSUSE (64 ビット) をインストールする

.NET Core 2.x for openSUSE または .NET Core 1.x for openSUSE (64 ビット) をインストールするには:

1. システムから**以前のプレビュー** バージョンの .NET Core を削除します。

> [!NOTE]
> tar.gz から Linux システムをインストールするには、ユーザー指定のディレクトリが必要です。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

2. Microsoft 署名キーを登録します。

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. dotnet 製品フィードを追加します。

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. .NET Core SDK をインストールします。

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. パスに dotnet を追加します。

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

2. 必須コンポーネントを取得します。

   ```bash
   sudo zypper install libunwind libicu
   ```

3. .NET Core SDK バイナリ (tarball) をダウンロードします。

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. .NET Core SDK バイナリを抽出します。
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. パスに dotnet を追加します。

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. `dotnet --version` コマンドを実行して、インストールが成功したことを確認します。

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> サポートされている Linux ディストリビューション/バージョンの .NET Core 2.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [2.0 の既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.0)を参照してください。 
>
> サポートされている Linux ディストリビューション/バージョンの .NET Core 1.x で問題が発生している場合は、インストールしたディストリビューション/バージョンに対する [1.0.0 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)と [1.0.1 の既知の問題](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)を参照してください。

