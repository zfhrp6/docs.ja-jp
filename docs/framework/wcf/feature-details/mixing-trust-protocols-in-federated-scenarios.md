---
title: "Trust プロトコルが混在するフェデレーション シナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7031e222b152bfa61e13e0e4a44b5ad9418b07c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="a6f10-102">Trust プロトコルが混在するフェデレーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="a6f10-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="a6f10-103">シナリオによっては、フェデレーション クライアントが、Trust バージョンの一致しないサービスやセキュリティ トークン サービス (STS: Security Token Service) と通信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6f10-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="a6f10-104">たとえば、サービス WSDL に、STS とは異なるバージョンの WS-Trust 要素を持つ `RequestSecurityTokenTemplate` アサーションが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="a6f10-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="a6f10-105">このような場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントは、`RequestSecurityTokenTemplate` から受け取った WS-Trust 要素を、STS Trust のバージョンに一致するように変換します。</span><span class="sxs-lookup"><span data-stu-id="a6f10-105">In such cases, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a6f10-106"> は、標準バインディングでのみ不一致の Trust バージョンを処理します。</span><span class="sxs-lookup"><span data-stu-id="a6f10-106"> handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="a6f10-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって認識されるすべての標準アルゴリズム パラメーターは、標準バインディングの一部です。</span><span class="sxs-lookup"><span data-stu-id="a6f10-107">All standard algorithm parameters that are recognized by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are part of the standard binding.</span></span> <span data-ttu-id="a6f10-108">このトピックでは、サービスと STS との間のさまざまな Trust 設定での [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6f10-108">This topic describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="a6f10-109">RP 2005/02 および STS 2005/02</span><span class="sxs-lookup"><span data-stu-id="a6f10-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="a6f10-110">証明書利用者 (RP: Relying Party) の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="a6f10-111">クライアント構成ファイルには、パラメーターのリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-111">The client configuration file contains a list of parameters.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a6f10-112"> では、クライアント パラメーターとサービス パラメーターを区別することはできません。すべてのパラメーターが追加され、`RequestSecurityTokenTemplate` (RST) で送信されます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-112"> cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="a6f10-113">RP Trust 1.3 および STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="a6f10-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="a6f10-114">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="a6f10-115">クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParameters` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a6f10-116">、`EncryptionAlgorithm`、および `CanonicalizationAlgorithm` の各要素が `KeyWrapAlgorithm` 要素の中に存在する場合、`SecondaryParameters` はこれらを RST の最上位の要素から削除します。</span><span class="sxs-lookup"><span data-stu-id="a6f10-116"> removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a6f10-117"> は、`SecondaryParameters` 要素を変更せずに送信 RST に追加します。</span><span class="sxs-lookup"><span data-stu-id="a6f10-117"> appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="a6f10-118">RP Trust 2005/02 および STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="a6f10-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="a6f10-119">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="a6f10-120">クライアント構成ファイルには、パラメーターのリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="a6f10-121">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、クライアント構成ファイルからサービス パラメーターとクライアント パラメーターを区別することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6f10-121">From the client configuration file, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="a6f10-122">このため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、すべてのパラメーターを Trust バージョン 1.3 の名前空間に変換します。</span><span class="sxs-lookup"><span data-stu-id="a6f10-122">Therefore [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a6f10-123"> は、`KeyType`、`KeySize`、および `TokenType` の各要素を次のように処理します。</span><span class="sxs-lookup"><span data-stu-id="a6f10-123"> handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="a6f10-124">WSDL をダウンロードし、バインディングを作成して、`KeyType`、`KeySize`、および `TokenType` を RP パラメーターから割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="a6f10-125">その後、クライアント構成ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="a6f10-126">この時点で、クライアントは構成ファイル内のパラメーターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="a6f10-127">実行時には、指定されたすべてのパラメーターが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によってクライアント構成ファイルの `AdditionalTokenParameters` セクションにコピーされます。ただし、`KeyType`、`KeySize`、および `TokenType` は構成ファイルの生成時に処理されるため、これらのパラメーターのコピーは行われません。</span><span class="sxs-lookup"><span data-stu-id="a6f10-127">During runtime, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="a6f10-128">RP Trust 1.3 および STS Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="a6f10-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="a6f10-129">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="a6f10-130">クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParamters` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6f10-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a6f10-131"> は、`SecondaryParameters` セクション内に指定されたすべてのパラメーターを最上位の RST 要素にコピーしますが、2005 WS-Trust の名前空間には変換しません。</span><span class="sxs-lookup"><span data-stu-id="a6f10-131"> copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
