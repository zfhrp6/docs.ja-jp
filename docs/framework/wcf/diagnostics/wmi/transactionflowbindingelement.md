---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa5394e874e35b80b01796642e18d69c71e867dc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="c39be-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="c39be-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="c39be-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="c39be-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c39be-104">構文</span><span class="sxs-lookup"><span data-stu-id="c39be-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c39be-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c39be-105">Methods</span></span>  
 <span data-ttu-id="c39be-106">TransactionFlowBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="c39be-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c39be-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c39be-107">Properties</span></span>  
 <span data-ttu-id="c39be-108">TransactionFlowBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c39be-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="c39be-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="c39be-109">IssuedTokens</span></span>  
 <span data-ttu-id="c39be-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="c39be-110">Data type: string</span></span>  
  
 <span data-ttu-id="c39be-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c39be-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c39be-112">発行されるセキュリティ トークン ヘッダー (WS-Trust からの IssuedTokens) の要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="c39be-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="c39be-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="c39be-113">TransactionProtocol</span></span>  
 <span data-ttu-id="c39be-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="c39be-114">Data type: string</span></span>  
  
 <span data-ttu-id="c39be-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c39be-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c39be-116">トランザクションをフローさせるためにサービスによって使用されるトランザクション プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="c39be-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="c39be-117">トランザクション</span><span class="sxs-lookup"><span data-stu-id="c39be-117">Transactions</span></span>  
 <span data-ttu-id="c39be-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c39be-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="c39be-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c39be-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c39be-120">受信トランザクションをサポートするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c39be-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c39be-121">要件</span><span class="sxs-lookup"><span data-stu-id="c39be-121">Requirements</span></span>  
  
|<span data-ttu-id="c39be-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c39be-122">MOF</span></span>|<span data-ttu-id="c39be-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c39be-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c39be-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="c39be-124">Namespace</span></span>|<span data-ttu-id="c39be-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c39be-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c39be-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="c39be-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
