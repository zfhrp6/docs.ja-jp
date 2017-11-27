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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="37c2e-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="37c2e-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="37c2e-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="37c2e-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c2e-104">構文</span><span class="sxs-lookup"><span data-stu-id="37c2e-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="37c2e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="37c2e-105">Methods</span></span>  
 <span data-ttu-id="37c2e-106">TransactionFlowBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="37c2e-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="37c2e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="37c2e-107">Properties</span></span>  
 <span data-ttu-id="37c2e-108">TransactionFlowBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="37c2e-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="37c2e-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="37c2e-109">IssuedTokens</span></span>  
 <span data-ttu-id="37c2e-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="37c2e-110">Data type: string</span></span>  
  
 <span data-ttu-id="37c2e-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="37c2e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37c2e-112">発行されるセキュリティ トークン ヘッダー (WS-Trust からの IssuedTokens) の要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="37c2e-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="37c2e-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="37c2e-113">TransactionProtocol</span></span>  
 <span data-ttu-id="37c2e-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="37c2e-114">Data type: string</span></span>  
  
 <span data-ttu-id="37c2e-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="37c2e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37c2e-116">トランザクションをフローさせるためにサービスによって使用されるトランザクション プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="37c2e-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="37c2e-117">トランザクション</span><span class="sxs-lookup"><span data-stu-id="37c2e-117">Transactions</span></span>  
 <span data-ttu-id="37c2e-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="37c2e-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="37c2e-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="37c2e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37c2e-120">受信トランザクションをサポートするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="37c2e-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37c2e-121">要件</span><span class="sxs-lookup"><span data-stu-id="37c2e-121">Requirements</span></span>  
  
|<span data-ttu-id="37c2e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="37c2e-122">MOF</span></span>|<span data-ttu-id="37c2e-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="37c2e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="37c2e-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="37c2e-124">Namespace</span></span>|<span data-ttu-id="37c2e-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="37c2e-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37c2e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="37c2e-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
