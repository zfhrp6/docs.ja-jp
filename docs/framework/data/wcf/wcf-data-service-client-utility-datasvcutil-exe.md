---
title: "WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, generating client data classes
- WCF Data Services, client library
- WCF Data Services, consuming
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 21189ffd5fc8b113cc746fd855bd5c325aad78c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-data-service-client-utility-datasvcutilexe"></a><span data-ttu-id="b645d-102">WCF Data Service クライアント ユーティリティ (DataSvcUtil.exe)</span><span class="sxs-lookup"><span data-stu-id="b645d-102">WCF Data Service Client Utility (DataSvcUtil.exe)</span></span>
<span data-ttu-id="b645d-103">DataSvcUtil.exe は、コマンド ライン ツールによって提供される[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]を消費する、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]フィードし、.NET Framework クライアント アプリケーションからデータ サービスにアクセスするために必要なクライアント データ サービス クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="b645d-103">DataSvcUtil.exe is a command-line tool provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] that consumes an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed and generates the client data service classes that are needed to access a data service from a .NET Framework client application.</span></span> <span data-ttu-id="b645d-104">このユーティリティでは、以下のメタデータ ソースを使用してデータ クラスを生成できます。</span><span class="sxs-lookup"><span data-stu-id="b645d-104">This utility can generate data classes by using the following metadata sources:</span></span>  
  
-   <span data-ttu-id="b645d-105">データ サービスのルート URI。</span><span class="sxs-lookup"><span data-stu-id="b645d-105">The root URI of a data service.</span></span> <span data-ttu-id="b645d-106">ユーティリティは、データ サービスによって公開されるデータ モデルが記述されたサービス メタデータ ドキュメントを要求します。</span><span class="sxs-lookup"><span data-stu-id="b645d-106">The utility requests the service metadata document, which describes the data model exposed by the data service.</span></span> <span data-ttu-id="b645d-107">詳細については、次を参照してください。 [OData: サービス メタデータ ドキュメント](http://go.microsoft.com/fwlink/?LinkId=186070)です。</span><span class="sxs-lookup"><span data-stu-id="b645d-107">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span>  
  
-   <span data-ttu-id="b645d-108">定義されている、概念スキーマ定義言語 (CSDL) を使用して定義されているデータ モデル ファイル (.csdl)、 [ \[MC-CSDL\]: 概念スキーマ定義ファイル形式](http://go.microsoft.com/fwlink/?LinkID=159072)仕様です。</span><span class="sxs-lookup"><span data-stu-id="b645d-108">A data model file (.csdl) defined by using the conceptual schema definition language (CSDL), as defined in the [\[MC-CSDL\]: Conceptual Schema Definition File Format](http://go.microsoft.com/fwlink/?LinkID=159072) specification.</span></span>  
  
-   <span data-ttu-id="b645d-109">Entity Framework に付属する Entity Data Model ツールを使用して作成された .edmx ファイル。</span><span class="sxs-lookup"><span data-stu-id="b645d-109">An .edmx file created by using the Entity Data Model tools that are provided with the Entity Framework.</span></span> <span data-ttu-id="b645d-110">詳細については、次を参照してください。、 [ \[MC-EDMX\]: データ サービスのパッケージ形式の Entity Data Model](http://go.microsoft.com/fwlink/?LinkID=178833)仕様です。</span><span class="sxs-lookup"><span data-stu-id="b645d-110">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification.</span></span>  
  
 <span data-ttu-id="b645d-111">詳細については、次を参照してください。[する方法: 手動で生成クライアント データ サービス クラス](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b645d-111">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="b645d-112">DataSvcUtil.exe ツールは [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ディレクトリにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="b645d-112">The DataSvcUtil.exe tool is installed in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] directory.</span></span> <span data-ttu-id="b645d-113">多くの場合、C:\Windows\Microsoft.NET\Framework\v4.0 にあります。</span><span class="sxs-lookup"><span data-stu-id="b645d-113">In many cases, this is located in C:\Windows\Microsoft.NET\Framework\v4.0,.</span></span> <span data-ttu-id="b645d-114">64 ビット システムの場合は、C:\Windows\Microsoft.NET\Framework64\v4.0 にあります。</span><span class="sxs-lookup"><span data-stu-id="b645d-114">For 64-bit systems, this is located in C:\Windows\Microsoft.NET\Framework64\v4.0.</span></span> <span data-ttu-id="b645d-115">Visual Studio コマンド プロンプトから DataSvcUtil.exe ツールをアクセスすることもできます (をクリックして**開始**、 をポイント**すべてのプログラム**、 をポイント**Microsoft Visual Studio 2010**、をポイント**Visual Studio Tools**、クリックして**Visual Studio 2010 コマンド プロンプト**)。</span><span class="sxs-lookup"><span data-stu-id="b645d-115">You can also access the DataSvcUtil.exe tool from the Visual Studio command prompt (Click **Start**, point to **All Programs**, point to **Microsoft Visual Studio 2010**, point to **Visual Studio Tools**, and then click **Visual Studio 2010 Command Prompt**).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b645d-116">構文</span><span class="sxs-lookup"><span data-stu-id="b645d-116">Syntax</span></span>  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b645d-117">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b645d-117">Parameters</span></span>  
  
|<span data-ttu-id="b645d-118">オプション</span><span class="sxs-lookup"><span data-stu-id="b645d-118">Option</span></span>|<span data-ttu-id="b645d-119">説明</span><span class="sxs-lookup"><span data-stu-id="b645d-119">Description</span></span>|  
|------------|-----------------|  
|`/dataservicecollection`|<span data-ttu-id="b645d-120">オブジェクトをコントロールにバインドするために必要なコードも生成することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b645d-120">Specifies that the code required to bind objects to controls is also generated.</span></span>|  
|`/help`<br /><br /> <span data-ttu-id="b645d-121">または</span><span class="sxs-lookup"><span data-stu-id="b645d-121">-or-</span></span><br /><br /> `/?`|<span data-ttu-id="b645d-122">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="b645d-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="b645d-123">`/in:`*\<ファイル >*</span><span class="sxs-lookup"><span data-stu-id="b645d-123">`/in:` *\<file>*</span></span>|<span data-ttu-id="b645d-124">.csdl ファイルまたは .edmx ファイル、またはファイルがあるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="b645d-124">Specifies the .csdl or .edmx file or a directory where the file is located.</span></span>|  
|<span data-ttu-id="b645d-125">`/language:`[VB &#124;です。CSharp]</span><span class="sxs-lookup"><span data-stu-id="b645d-125">`/language:`[VB&#124;CSharp]</span></span>|<span data-ttu-id="b645d-126">生成されるソース コード ファイルの言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="b645d-126">Specifies the language for the generated source code files.</span></span> <span data-ttu-id="b645d-127">既定の言語は C# です。</span><span class="sxs-lookup"><span data-stu-id="b645d-127">The language defaults to C#.</span></span>|  
|`/nologo`|<span data-ttu-id="b645d-128">著作権メッセージが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="b645d-128">Suppresses the copyright message from displaying.</span></span>|  
|<span data-ttu-id="b645d-129">`/out:`*\<ファイル >*</span><span class="sxs-lookup"><span data-stu-id="b645d-129">`/out:` *\<file>*</span></span>|<span data-ttu-id="b645d-130">生成されたクライアント データ サービス クラスを含むソース コード ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="b645d-130">Specifies the name of the source code file that contains the generated client data service classes.</span></span>|  
|<span data-ttu-id="b645d-131">`/uri:`*\<文字列 >*</span><span class="sxs-lookup"><span data-stu-id="b645d-131">`/uri:` *\<string>*</span></span>|<span data-ttu-id="b645d-132">URI、[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。</span><span class="sxs-lookup"><span data-stu-id="b645d-132">The URI of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span>|  
|<span data-ttu-id="b645d-133">`/version:`[1.0&#124;2.0]</span><span class="sxs-lookup"><span data-stu-id="b645d-133">`/version:`[1.0&#124;2.0]</span></span>|<span data-ttu-id="b645d-134">許容される [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] の最上位バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="b645d-134">Specifies the highest accepted version of [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span> <span data-ttu-id="b645d-135">基に、バージョンが決定されます、`DataServiceVersion`返されたデータ サービス メタデータの DataService 要素の属性です。</span><span class="sxs-lookup"><span data-stu-id="b645d-135">The version is determined based on the `DataServiceVersion` attribute of the DataService element in the returned data service metadata.</span></span> <span data-ttu-id="b645d-136">詳細については、次を参照してください。[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="b645d-136">For more information, see [Data Service Versioning](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).</span></span> <span data-ttu-id="b645d-137">指定すると、`/dataservicecollection`パラメーターも指定してください`/version:2.0`データ バインディングを有効にします。</span><span class="sxs-lookup"><span data-stu-id="b645d-137">When you specify the `/dataservicecollection` parameter, you must also specify `/version:2.0` to enable data binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b645d-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="b645d-138">See Also</span></span>  
 [<span data-ttu-id="b645d-139">データ サービス クライアント ライブラリの生成</span><span class="sxs-lookup"><span data-stu-id="b645d-139">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 [<span data-ttu-id="b645d-140">方法: データ サービス参照の追加</span><span class="sxs-lookup"><span data-stu-id="b645d-140">How to: Add a Data Service Reference</span></span>](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
