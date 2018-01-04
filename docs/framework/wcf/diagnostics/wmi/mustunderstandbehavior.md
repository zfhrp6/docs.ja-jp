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
ms.workload: dotnet
ms.openlocfilehash: 9b6838c6ce98e0d373a45c136b12bdedbd8c9eb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="2f971-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="2f971-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="2f971-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="2f971-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f971-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f971-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2f971-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2f971-105">Methods</span></span>  
 <span data-ttu-id="2f971-106">MustUnderstandBehavior クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="2f971-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2f971-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2f971-107">Properties</span></span>  
 <span data-ttu-id="2f971-108">MustUnderstandBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="2f971-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="2f971-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="2f971-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="2f971-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="2f971-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2f971-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="2f971-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2f971-112">`true` の場合、未処理の `MustUnderstand` 属性を持つすべての SOAP ヘッダーは、動作が例外をスローする原因となります。</span><span class="sxs-lookup"><span data-stu-id="2f971-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f971-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="2f971-113">Requirements</span></span>  
  
|<span data-ttu-id="2f971-114">MOF</span><span class="sxs-lookup"><span data-stu-id="2f971-114">MOF</span></span>|<span data-ttu-id="2f971-115">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="2f971-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2f971-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="2f971-116">Namespace</span></span>|<span data-ttu-id="2f971-117">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="2f971-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f971-118">参照</span><span class="sxs-lookup"><span data-stu-id="2f971-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
