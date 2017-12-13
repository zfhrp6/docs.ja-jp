---
title: "FindPrivateKey サンプルの WCF"
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29489cd1b82cf1c31f178d8a305a21371b542f15
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2017
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="b2c6a-102">FindPrivateKey サンプル</span><span class="sxs-lookup"><span data-stu-id="b2c6a-102">FindPrivateKey sample</span></span>

<span data-ttu-id="b2c6a-103">証明書ストア内の特定の X.509 証明書に関連付けられている秘密キー ファイルの場所と名前を見つけることが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="b2c6a-104">FindPrivateKey.exe ツールを使用すると、この処理を容易に実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2c6a-105">FindPrivateKey は、使用する前にコンパイルする必要があるサンプルです。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="b2c6a-106">参照してください、 [FindPrivateKey プロジェクトをビルドする](#to-build-the-findprivatekey-project)FindPrivateKey ツールを構築する方法の手順についてのセクションです。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="b2c6a-107">X.509 証明書は、コンピューターの管理者または任意のユーザーによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="b2c6a-108">ただし、証明書は、別のアカウントで実行されているサービスによってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="b2c6a-109">たとえば、ネットワーク サービス アカウント。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="b2c6a-110">別のアカウントでは、秘密キー ファイルへアクセスできない場合があります。これは、証明書が最初にこのアカウントによってインストールされていないからです。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="b2c6a-111">FindPrivateKey ツールでは、指定された X.509 証明書の秘密キー ファイルの場所を検索できます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="b2c6a-112">特定の X.509 証明書の秘密キー ファイルの場所がわかれば、このファイルに対するアクセス許可の追加または削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="b2c6a-113">セキュリティ証明書を使用したサンプルの FindPrivateKey ツールを使用して、 *Setup.bat*ファイル。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="b2c6a-114">秘密キー ファイルが見つかったら、その他のツールをなど、使用できる*Cacls.exe*をファイルに適切なアクセス権を設定します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="b2c6a-115">自己ホスト型の実行可能ファイルなどのユーザー アカウントで Windows Communication Foundation (WCF) サービスを実行している場合は、ユーザー アカウントが、ファイルに読み取り専用アクセス権を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="b2c6a-116">インターネット インフォメーション サービス (IIS) WCF サービスを実行するときに、サービスを実行する既定のアカウントは IIS 7 と以前のバージョンで、ネットワーク サービスまたは IIS 7.5、およびそれ以降のバージョンのアプリケーション プール Id です。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="b2c6a-117">詳細については、次を参照してください。[アプリケーション プール Id](/iis/manage/configuring-security/application-pool-identities)です。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="b2c6a-118">例</span><span class="sxs-lookup"><span data-stu-id="b2c6a-118">Examples</span></span>

<span data-ttu-id="b2c6a-119">対象のプロセスは読み取り特権がない証明書にアクセスするときに次の例のような例外メッセージを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="b2c6a-120">この場合、FindPrivateKey ツールを使用して、秘密キー ファイルを検索およびサービスが実行されているプロセスにアクセス権を設定します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="b2c6a-121">たとえば、これ行う Cacls.exe ツールを使用して、次の例に示すように。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="b2c6a-122">FindPrivateKey プロジェクトをビルドするには</span><span class="sxs-lookup"><span data-stu-id="b2c6a-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="b2c6a-123">プロジェクトをダウンロードするには、次を参照してください。 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)です。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="b2c6a-124">開いている[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]に移動し、 *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS*サンプルがインストールされているディレクトリの場所の下のフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-124">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="b2c6a-125">.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="b2c6a-126">**ビルド**メニューの **ソリューションのリビルド**です。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="b2c6a-127">ソリューションをビルドすると、FindPrivateKey.exe ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="b2c6a-128">規則-コマンドラインのエントリ</span><span class="sxs-lookup"><span data-stu-id="b2c6a-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="b2c6a-129">"[*オプション*]"オプションのパラメーターのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="b2c6a-130">"{*オプション*}"必須のパラメーターのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="b2c6a-131">"*option1* &#124;です。*・ オプション 2*"オプションのセットのいずれかを表します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="b2c6a-132">"\<*値*>"を入力するパラメーター値を表します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="b2c6a-133">使用方法</span><span class="sxs-lookup"><span data-stu-id="b2c6a-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="b2c6a-134">この場合、</span><span class="sxs-lookup"><span data-stu-id="b2c6a-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="b2c6a-135">コマンド プロンプト パラメーターが指定されていない場合は、このヘルプ テキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="b2c6a-136">例</span><span class="sxs-lookup"><span data-stu-id="b2c6a-136">Examples</span></span>

<span data-ttu-id="b2c6a-137">この例は、証明書のサブジェクト名を持つファイル名を検索"CN = localhost"、現在のユーザーの個人用ストアにします。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="b2c6a-138">この例は、証明書のサブジェクト名を持つファイル名を検索"CN = localhost"、個人用で、現在のユーザーのストアし、出力ディレクトリの完全パス。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="b2c6a-139">この例では、ローカル コンピューターの Personal ストアで、"03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" というサムプリントを持つ証明書のファイル名を検索します。</span><span class="sxs-lookup"><span data-stu-id="b2c6a-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
