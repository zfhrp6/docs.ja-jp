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
ms.openlocfilehash: ab341f55947bfcfbc776143e3bbc33e125da89c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="e1c26-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e1c26-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="e1c26-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e1c26-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c26-104">構文</span><span class="sxs-lookup"><span data-stu-id="e1c26-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e1c26-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e1c26-105">Methods</span></span>  
 <span data-ttu-id="e1c26-106">SymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="e1c26-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e1c26-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e1c26-107">Properties</span></span>  
 <span data-ttu-id="e1c26-108">SymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="e1c26-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="e1c26-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="e1c26-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="e1c26-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="e1c26-110">Data type: string</span></span>  
  
 <span data-ttu-id="e1c26-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e1c26-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1c26-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="e1c26-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="e1c26-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="e1c26-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="e1c26-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="e1c26-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e1c26-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="e1c26-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1c26-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="e1c26-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1c26-117">要件</span><span class="sxs-lookup"><span data-stu-id="e1c26-117">Requirements</span></span>  
  
|<span data-ttu-id="e1c26-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e1c26-118">MOF</span></span>|<span data-ttu-id="e1c26-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="e1c26-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e1c26-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="e1c26-120">Namespace</span></span>|<span data-ttu-id="e1c26-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="e1c26-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1c26-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1c26-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
