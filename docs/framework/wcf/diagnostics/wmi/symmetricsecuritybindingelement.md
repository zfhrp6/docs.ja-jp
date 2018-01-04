---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="c4d4c-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c4d4c-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="c4d4c-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c4d4c-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d4c-104">構文</span><span class="sxs-lookup"><span data-stu-id="c4d4c-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c4d4c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c4d4c-105">Methods</span></span>  
 <span data-ttu-id="c4d4c-106">SymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="c4d4c-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c4d4c-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c4d4c-107">Properties</span></span>  
 <span data-ttu-id="c4d4c-108">SymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c4d4c-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="c4d4c-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="c4d4c-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="c4d4c-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="c4d4c-110">Data type: string</span></span>  
  
 <span data-ttu-id="c4d4c-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4d4c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4d4c-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="c4d4c-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="c4d4c-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="c4d4c-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="c4d4c-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="c4d4c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c4d4c-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c4d4c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c4d4c-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="c4d4c-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d4c-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="c4d4c-117">Requirements</span></span>  
  
|<span data-ttu-id="c4d4c-118">MOF</span><span class="sxs-lookup"><span data-stu-id="c4d4c-118">MOF</span></span>|<span data-ttu-id="c4d4c-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c4d4c-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c4d4c-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="c4d4c-120">Namespace</span></span>|<span data-ttu-id="c4d4c-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c4d4c-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4d4c-122">参照</span><span class="sxs-lookup"><span data-stu-id="c4d4c-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
