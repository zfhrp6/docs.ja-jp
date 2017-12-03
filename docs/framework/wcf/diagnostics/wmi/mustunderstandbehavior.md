---
title: MustUnderstandBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 40075acb2a098c98b4cd0ab35f213981c09f8486
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="8b2ff-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="8b2ff-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="8b2ff-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="8b2ff-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b2ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b2ff-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8b2ff-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8b2ff-105">Methods</span></span>  
 <span data-ttu-id="8b2ff-106">MustUnderstandBehavior クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="8b2ff-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8b2ff-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8b2ff-107">Properties</span></span>  
 <span data-ttu-id="8b2ff-108">MustUnderstandBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8b2ff-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="8b2ff-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="8b2ff-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="8b2ff-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="8b2ff-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8b2ff-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8b2ff-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8b2ff-112">`true` の場合、未処理の `MustUnderstand` 属性を持つすべての SOAP ヘッダーは、動作が例外をスローする原因となります。</span><span class="sxs-lookup"><span data-stu-id="8b2ff-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b2ff-113">要件</span><span class="sxs-lookup"><span data-stu-id="8b2ff-113">Requirements</span></span>  
  
|<span data-ttu-id="8b2ff-114">MOF</span><span class="sxs-lookup"><span data-stu-id="8b2ff-114">MOF</span></span>|<span data-ttu-id="8b2ff-115">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="8b2ff-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8b2ff-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="8b2ff-116">Namespace</span></span>|<span data-ttu-id="8b2ff-117">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="8b2ff-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b2ff-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b2ff-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
