---
title: FindPrivateKey サンプルの WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 72e2f49ae7c39b4a0486ec053ff1164c2d833cbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501662"
---
# <a name="findprivatekey-sample"></a>FindPrivateKey サンプル

証明書ストア内の特定の X.509 証明書に関連付けられている秘密キー ファイルの場所と名前を見つけることが困難な場合があります。 FindPrivateKey.exe ツールを使用すると、この処理を容易に実行できます。

> [!IMPORTANT]
> FindPrivateKey は、使用する前にコンパイルする必要があるサンプルです。 参照してください、 [FindPrivateKey プロジェクトをビルドする](#to-build-the-findprivatekey-project)FindPrivateKey ツールを構築する方法の手順についてのセクションです。

X.509 証明書は、コンピューターの管理者または任意のユーザーによってインストールされます。 ただし、証明書は、別のアカウントで実行されているサービスによってアクセスできます。 たとえば、ネットワーク サービス アカウント。

別のアカウントでは、秘密キー ファイルへアクセスできない場合があります。これは、証明書が最初にこのアカウントによってインストールされていないからです。 FindPrivateKey ツールでは、指定された X.509 証明書の秘密キー ファイルの場所を検索できます。 特定の X.509 証明書の秘密キー ファイルの場所がわかれば、このファイルに対するアクセス許可の追加または削除を実行できます。

セキュリティ証明書を使用したサンプルの FindPrivateKey ツールを使用して、 *Setup.bat*ファイル。 秘密キー ファイルが見つかったら、その他のツールをなど、使用できる*Cacls.exe*をファイルに適切なアクセス権を設定します。

自己ホスト型の実行可能ファイルなどのユーザー アカウントで Windows Communication Foundation (WCF) サービスを実行している場合は、ユーザー アカウントが、ファイルに読み取り専用アクセス権を持っていることを確認します。 インターネット インフォメーション サービス (IIS) WCF サービスを実行するときに、サービスを実行する既定のアカウントは IIS 7 と以前のバージョンで、ネットワーク サービスまたは IIS 7.5、およびそれ以降のバージョンのアプリケーション プール Id です。 詳細については、次を参照してください。[アプリケーション プール Id](/iis/manage/configuring-security/application-pool-identities)です。

## <a name="examples"></a>使用例

対象のプロセスは読み取り特権がない証明書にアクセスするときに次の例のような例外メッセージを参照してください。

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

この場合、FindPrivateKey ツールを使用して、秘密キー ファイルを検索およびサービスが実行されているプロセスにアクセス権を設定します。 たとえば、これ行う Cacls.exe ツールを使用して、次の例に示すように。

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>FindPrivateKey プロジェクトをビルドするには

プロジェクトをダウンロードするには、次を参照してください。 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)です。

1. 開いている[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]に移動し、 *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS*サンプルがインストールされているディレクトリの場所の下のフォルダーです。

2. .sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。

3. **ビルド**メニューの **ソリューションのリビルド**です。

4. ソリューションをビルドすると、FindPrivateKey.exe ファイルが生成されます。

## <a name="conventionscommand-line-entries"></a>規則-コマンドラインのエントリ

 "[*オプション*]"オプションのパラメーターのセットを表します。

 "{*オプション*}"必須のパラメーターのセットを表します。

 "*option1* &#124; *・ オプション 2*"オプションのセットのいずれかを表します。

 "\<*値*>"を入力するパラメーター値を表します。

## <a name="usage"></a>使用法

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

この場合、

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

コマンド プロンプト パラメーターが指定されていない場合は、このヘルプ テキストが表示されます。

## <a name="examples"></a>使用例

この例は、証明書のサブジェクト名を持つファイル名を検索"CN = localhost"、現在のユーザーの個人用ストアにします。

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

この例は、証明書のサブジェクト名を持つファイル名を検索"CN = localhost"、個人用で、現在のユーザーのストアし、出力ディレクトリの完全パス。

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

この例では、ローカル コンピューターの Personal ストアで、"03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" というサムプリントを持つ証明書のファイル名を検索します。

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
