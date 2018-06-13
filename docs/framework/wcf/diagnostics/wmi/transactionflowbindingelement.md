---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: c2fb32c4c693cbfc487ce89b36f013398cbdb703
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485621"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="34b8f-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="34b8f-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="34b8f-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="34b8f-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34b8f-104">構文</span><span class="sxs-lookup"><span data-stu-id="34b8f-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="34b8f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="34b8f-105">Methods</span></span>  
 <span data-ttu-id="34b8f-106">TransactionFlowBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="34b8f-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="34b8f-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34b8f-107">Properties</span></span>  
 <span data-ttu-id="34b8f-108">TransactionFlowBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="34b8f-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="34b8f-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="34b8f-109">IssuedTokens</span></span>  
 <span data-ttu-id="34b8f-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="34b8f-110">Data type: string</span></span>  
  
 <span data-ttu-id="34b8f-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="34b8f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="34b8f-112">発行されるセキュリティ トークン ヘッダー (WS-Trust からの IssuedTokens) の要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="34b8f-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="34b8f-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="34b8f-113">TransactionProtocol</span></span>  
 <span data-ttu-id="34b8f-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="34b8f-114">Data type: string</span></span>  
  
 <span data-ttu-id="34b8f-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="34b8f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="34b8f-116">トランザクションをフローさせるためにサービスによって使用されるトランザクション プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="34b8f-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="34b8f-117">トランザクション</span><span class="sxs-lookup"><span data-stu-id="34b8f-117">Transactions</span></span>  
 <span data-ttu-id="34b8f-118">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="34b8f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="34b8f-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="34b8f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="34b8f-120">受信トランザクションをサポートするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="34b8f-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34b8f-121">要件</span><span class="sxs-lookup"><span data-stu-id="34b8f-121">Requirements</span></span>  
  
|<span data-ttu-id="34b8f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="34b8f-122">MOF</span></span>|<span data-ttu-id="34b8f-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="34b8f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="34b8f-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="34b8f-124">Namespace</span></span>|<span data-ttu-id="34b8f-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="34b8f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34b8f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="34b8f-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
