---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fc720f4f0be25a0cec25d979942af8472efa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485057"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="15f0a-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="15f0a-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="15f0a-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="15f0a-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f0a-104">構文</span><span class="sxs-lookup"><span data-stu-id="15f0a-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="15f0a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="15f0a-105">Methods</span></span>  
 <span data-ttu-id="15f0a-106">SymmetricSecurityBindingElement クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="15f0a-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="15f0a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="15f0a-107">Properties</span></span>  
 <span data-ttu-id="15f0a-108">SymmetricSecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="15f0a-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="15f0a-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="15f0a-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="15f0a-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="15f0a-110">Data type: string</span></span>  
  
 <span data-ttu-id="15f0a-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15f0a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15f0a-112">このバインディングのメッセージの暗号化と署名の命令。</span><span class="sxs-lookup"><span data-stu-id="15f0a-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="15f0a-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="15f0a-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="15f0a-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="15f0a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="15f0a-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="15f0a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15f0a-116">バインディングで署名の確認が必要かどうか。</span><span class="sxs-lookup"><span data-stu-id="15f0a-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15f0a-117">要件</span><span class="sxs-lookup"><span data-stu-id="15f0a-117">Requirements</span></span>  
  
|<span data-ttu-id="15f0a-118">MOF</span><span class="sxs-lookup"><span data-stu-id="15f0a-118">MOF</span></span>|<span data-ttu-id="15f0a-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="15f0a-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="15f0a-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="15f0a-120">Namespace</span></span>|<span data-ttu-id="15f0a-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="15f0a-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15f0a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="15f0a-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
