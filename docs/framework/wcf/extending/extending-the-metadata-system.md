---
title: "メタデータ システムの拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending metadata [WCF]
ms.assetid: 8c6b3b00-61b8-4589-8fa5-546cc33719bf
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aca7a7aba7ef4a40100e9858561d197916b71544
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-metadata-system"></a><span data-ttu-id="700ba-102">メタデータ システムの拡張</span><span class="sxs-lookup"><span data-stu-id="700ba-102">Extending the Metadata System</span></span>
<span data-ttu-id="700ba-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメタデータ システムは複数のクラスのグループおよびインターフェイスで、サービス ベースのアプリケーションを実装するために必要なメタデータを表します。</span><span class="sxs-lookup"><span data-stu-id="700ba-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="700ba-104">クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。</span><span class="sxs-lookup"><span data-stu-id="700ba-104">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="700ba-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="700ba-105">In This Section</span></span>  
 [<span data-ttu-id="700ba-106">WCF 拡張に対するカスタム メタデータのエクスポート</span><span class="sxs-lookup"><span data-stu-id="700ba-106">Exporting Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/exporting-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="700ba-107"><xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、カスタム ポリシー アサーションを WSDL ドキュメントに埋め込む方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="700ba-107">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface to embed custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="700ba-108">WCF 拡張に対するカスタム メタデータのインポート</span><span class="sxs-lookup"><span data-stu-id="700ba-108">Importing Custom Metadata for a WCF Extension</span></span>](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)  
 <span data-ttu-id="700ba-109"><xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> インターフェイスを実装および使用して、WSDL ドキュメント内のカスタム ポリシー アサーションの読み取りや応答を行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="700ba-109">Describes how to implement and use the <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> interface to read and respond to custom policy assertions in WSDL documents.</span></span>  
  
 [<span data-ttu-id="700ba-110">カスタム バインディングを介したメタデータの公開と取得</span><span class="sxs-lookup"><span data-stu-id="700ba-110">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 <span data-ttu-id="700ba-111">カスタム バインドを介してメタデータを交換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="700ba-111">Describes how to exchange metadata over custom bindings.</span></span>
