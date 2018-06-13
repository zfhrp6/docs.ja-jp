---
title: Trust プロトコルが混在するフェデレーション シナリオ
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494465"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="59a5e-102">Trust プロトコルが混在するフェデレーション シナリオ</span><span class="sxs-lookup"><span data-stu-id="59a5e-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="59a5e-103">シナリオによっては、フェデレーション クライアントが、Trust バージョンの一致しないサービスやセキュリティ トークン サービス (STS: Security Token Service) と通信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="59a5e-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="59a5e-104">たとえば、サービス WSDL に、STS とは異なるバージョンの WS-Trust 要素を持つ `RequestSecurityTokenTemplate` アサーションが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="59a5e-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="59a5e-105">このような場合は、Windows Communication Foundation (WCF) クライアントから受け取った Ws-trust 要素に変換します、 `RequestSecurityTokenTemplate` STS trust のバージョンと一致します。</span><span class="sxs-lookup"><span data-stu-id="59a5e-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="59a5e-106">WCF では、標準バインディングでのみ不一致の trust バージョンを処理します。</span><span class="sxs-lookup"><span data-stu-id="59a5e-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="59a5e-107">WCF で認識されるすべての標準アルゴリズム パラメーターは、標準バインディングの一部です。</span><span class="sxs-lookup"><span data-stu-id="59a5e-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="59a5e-108">このトピックでは、さまざまな信頼の設定、サービスと STS との間での WCF 動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="59a5e-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="59a5e-109">RP 2005/02 および STS 2005/02</span><span class="sxs-lookup"><span data-stu-id="59a5e-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="59a5e-110">証明書利用者 (RP: Relying Party) の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="59a5e-111">クライアント構成ファイルには、パラメーターのリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="59a5e-112">WCF は、クライアントとサービスのパラメーターを区別できません。すべてのパラメーターを追加で送信され、 `RequestSecurityTokenTemplate` (RST)。</span><span class="sxs-lookup"><span data-stu-id="59a5e-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="59a5e-113">RP Trust 1.3 および STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="59a5e-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="59a5e-114">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="59a5e-115">クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParameters` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="59a5e-116">WCF の削除、 `EncryptionAlgorithm`、`CanonicalizationAlgorithm`と`KeyWrapAlgorithm`RST これらの中に存在する場合、最上位の要素からの要素、`SecondaryParameters`要素。</span><span class="sxs-lookup"><span data-stu-id="59a5e-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="59a5e-117">WCF の追加、`SecondaryParameters`くだ送信 RST 要素。</span><span class="sxs-lookup"><span data-stu-id="59a5e-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="59a5e-118">RP Trust 2005/02 および STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="59a5e-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="59a5e-119">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="59a5e-120">クライアント構成ファイルには、パラメーターのリストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="59a5e-121">クライアント構成ファイルから WCF は、サービスとクライアント パラメーターを区別できません。</span><span class="sxs-lookup"><span data-stu-id="59a5e-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="59a5e-122">したがって WCF では、すべてのパラメーターが信頼バージョン 1.3 の名前空間に変換します。</span><span class="sxs-lookup"><span data-stu-id="59a5e-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="59a5e-123">WCF ハンドル、 `KeyType`、 `KeySize`、および`TokenType`要素は次のようにします。</span><span class="sxs-lookup"><span data-stu-id="59a5e-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="59a5e-124">WSDL をダウンロードし、バインディングを作成して、`KeyType`、`KeySize`、および `TokenType` を RP パラメーターから割り当てます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="59a5e-125">その後、クライアント構成ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="59a5e-126">この時点で、クライアントは構成ファイル内のパラメーターを変更できます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="59a5e-127">実行時に WCF コピーに指定されたすべてのパラメーター、 `AdditionalTokenParameters` 、クライアント構成ファイルのセクションを除く`KeyType`、`KeySize`と`TokenType`これらのパラメーターは、構成ファイル中に考慮するため、生成します。</span><span class="sxs-lookup"><span data-stu-id="59a5e-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="59a5e-128">RP Trust 1.3 および STS Trust 2005/02</span><span class="sxs-lookup"><span data-stu-id="59a5e-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="59a5e-129">RP の WSDL には、`RequestSecurityTokenTemplate` セクション内に次の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="59a5e-130">クライアント構成ファイルには、RP によって指定されたパラメーターをラップする `secondaryParamters` 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="59a5e-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="59a5e-131">WCF コピー内で指定されたすべてのパラメーター、 `SecondaryParameters` RST の最上位の要素のセクションは、2005 Ws-trust 名前空間に変換しません。</span><span class="sxs-lookup"><span data-stu-id="59a5e-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
