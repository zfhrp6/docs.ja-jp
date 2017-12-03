---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ca357ccdcbe76f36f3ba56caf2013a80143728
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="findprivatekey"></a><span data-ttu-id="84dc4-102">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="84dc4-102">FindPrivateKey</span></span>
<span data-ttu-id="84dc4-103">証明書ストア内の特定の X.509 証明書に関連付けられている秘密キー ファイルの場所と名前を見つけることが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="84dc4-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="84dc4-104">FindPrivateKey.exe ツールを使用すると、この処理を容易に実行できます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-104">The FindPrivateKey.exe tool facilitates this process.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="84dc4-105">FindPrivateKey は、使用する前にコンパイルする必要があるサンプルです。</span><span class="sxs-lookup"><span data-stu-id="84dc4-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="84dc4-106">FindPrivateKey ツールを構築する方法の FindPrivateKey プロジェクトをビルドするには"するには"以下のセクションの手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84dc4-106">See the "To build the FindPrivateKey project" section below for instructions on how to build the FindPrivateKey tool.</span></span>  
  
 <span data-ttu-id="84dc4-107">X.509 証明書は、コンピューターの管理者または任意のユーザーによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="84dc4-108">ただし、証明書は別のアカウント ([!INCLUDE[wxp](../../../../includes/wxp-md.md)] の ASPNET、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] の NETWORK SERVICE アカウントなど) で実行されているサービスからアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-108">However the certificate may be accessed by a service running under a different account (for example, the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE accounts on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span></span>  
  
 <span data-ttu-id="84dc4-109">別のアカウントでは、秘密キー ファイルへアクセスできない場合があります。これは、証明書が最初にこのアカウントによってインストールされていないからです。</span><span class="sxs-lookup"><span data-stu-id="84dc4-109">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="84dc4-110">FindPrivateKey ツールでは、指定された X.509 証明書の秘密キー ファイルの場所を検索できます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-110">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="84dc4-111">特定の X.509 証明書の秘密キー ファイルの場所がわかれば、このファイルに対するアクセス許可の追加または削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-111">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>  
  
 <span data-ttu-id="84dc4-112">セキュリティ用の証明書を使用するこのサンプルでは、Setup.bat ファイル内の FindPrivateKey ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-112">The samples that use certificates for security use the FindPrivateKey tool in the Setup.bat file.</span></span> <span data-ttu-id="84dc4-113">秘密キー ファイルが見つかったら、Cacls.exe などの別のツールを使用して、このファイルに対する適切なアクセス権を設定できます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-113">Once the private key file has been found you can use other tools such as Cacls.exe to set the appropriate access rights onto the file.</span></span>  
  
 <span data-ttu-id="84dc4-114">自己ホスト型の実行可能ファイルなどの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをユーザー アカウントで実行している場合は、そのユーザー アカウントがそのファイルへの読み取り専用のアクセス権限を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-114">When running a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="84dc4-115">インターネット インフォメーション サービス (IIS) で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを実行している場合、サービスが実行されている既定のアカウントは、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] では ASPNET、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では NETWORK SERVICE です。これらのアカウントには、既定では秘密キー ファイルへのアクセス権限がありません。</span><span class="sxs-lookup"><span data-stu-id="84dc4-115">When running a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under Internet Information Services (IIS) the default accounts that the service runs under are the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], which by default do not have access to the private key file.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="84dc4-116">例</span><span class="sxs-lookup"><span data-stu-id="84dc4-116">Examples</span></span>  
 <span data-ttu-id="84dc4-117">証明書にアクセスする際、プロセスにその証明書に対する読み取り権限がない場合、次の例のような例外メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-117">When accessing a certificate for which the process does not have read privilege, you see an exception message similar to the following example.</span></span>  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 <span data-ttu-id="84dc4-118">この例外が発生したら、FindPrivateKey ツールを使用して秘密キー ファイルを検索し、サービスが実行されているプロセスにアクセス権を設定します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-118">When this occurs use the FindPrivateKey tool to find the private key file and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="84dc4-119">たとえば、次の例に示すように、Cacls.exe ツールを使用して処理できます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-119">For example, this can be done with the Cacls.exe tool as shown in the following example.</span></span>  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="84dc4-120">FindPrivateKey プロジェクトをビルドするには</span><span class="sxs-lookup"><span data-stu-id="84dc4-120">To build the FindPrivateKey project</span></span>  
  
1.  <span data-ttu-id="84dc4-121">[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]を開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-121">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="84dc4-122">.sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-122">Double-click the .sln file icon to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="84dc4-123">**ビルド**メニューの **ソリューションのリビルド**です。</span><span class="sxs-lookup"><span data-stu-id="84dc4-123">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="84dc4-124">クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-124">The client program files are built to client\bin and the service program files are built to service\bin.</span></span>  
  
4.  <span data-ttu-id="84dc4-125">ソリューションをビルドすると、FindPrivateKey.exe ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-125">Building the solution generates the file: FindPrivateKey.exe.</span></span>  
  
## <a name="conventionscommand-line-entries"></a><span data-ttu-id="84dc4-126">規則 - コマンド ラインのエントリ</span><span class="sxs-lookup"><span data-stu-id="84dc4-126">Conventions—Command-Line Entries</span></span>  
 <span data-ttu-id="84dc4-127">"[*オプション*]"オプションのパラメーターのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-127">"[*option*]" represents an optional set of parameters.</span></span>  
  
 <span data-ttu-id="84dc4-128">"{*オプション*}"必須のパラメーターのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-128">"{*option*}" represents a mandatory set of parameters.</span></span>  
  
 <span data-ttu-id="84dc4-129">"*option1* &#124;です。*・ オプション 2*"オプションのセットのいずれかを表します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-129">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>  
  
 <span data-ttu-id="84dc4-130">"\<*値*>"を入力するパラメーター値を表します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-130">"\<*value*>" represents a parameter value to be entered.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="84dc4-131">使用方法</span><span class="sxs-lookup"><span data-stu-id="84dc4-131">Usage</span></span>  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 <span data-ttu-id="84dc4-132">指定項目:</span><span class="sxs-lookup"><span data-stu-id="84dc4-132">Where:</span></span>  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 <span data-ttu-id="84dc4-133">コマンド プロンプトでパラメーターを指定しない場合、このヘルプ テキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84dc4-133">If no parameters are specified at the command prompt then this help text is displayed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="84dc4-134">例</span><span class="sxs-lookup"><span data-stu-id="84dc4-134">Examples</span></span>  
 <span data-ttu-id="84dc4-135">この例では、現在のユーザーの Personal ストアで、"CN=localhost" というサブジェクト名を持つ証明書のファイル名を検索します (FindPrivateKey My CurrentUser -n "CN=localhost")。</span><span class="sxs-lookup"><span data-stu-id="84dc4-135">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.FindPrivateKey My CurrentUser -n "CN=localhost".</span></span>  
  
 <span data-ttu-id="84dc4-136">この例では、現在のユーザーの Personal ストアで、"CN=localhost" というサブジェクト名を持つ証明書のファイル名を検索し、ディレクトリの完全パスを出力します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-136">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current and output the full directory path.</span></span>  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 <span data-ttu-id="84dc4-137">この例では、ローカル コンピューターの Personal ストアで、"03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" というサムプリントを持つ証明書のファイル名を検索します。</span><span class="sxs-lookup"><span data-stu-id="84dc4-137">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="84dc4-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="84dc4-138">See Also</span></span>
