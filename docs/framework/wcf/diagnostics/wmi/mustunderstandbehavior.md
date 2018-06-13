---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 14150a992130e9ed4734c950d4ed92f1bbd3206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485558"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="1730f-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="1730f-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="1730f-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="1730f-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1730f-104">構文</span><span class="sxs-lookup"><span data-stu-id="1730f-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1730f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1730f-105">Methods</span></span>  
 <span data-ttu-id="1730f-106">MustUnderstandBehavior クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="1730f-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1730f-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1730f-107">Properties</span></span>  
 <span data-ttu-id="1730f-108">MustUnderstandBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="1730f-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="1730f-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="1730f-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="1730f-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="1730f-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="1730f-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="1730f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1730f-112">`true` の場合、未処理の `MustUnderstand` 属性を持つすべての SOAP ヘッダーは、動作が例外をスローする原因となります。</span><span class="sxs-lookup"><span data-stu-id="1730f-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1730f-113">要件</span><span class="sxs-lookup"><span data-stu-id="1730f-113">Requirements</span></span>  
  
|<span data-ttu-id="1730f-114">MOF</span><span class="sxs-lookup"><span data-stu-id="1730f-114">MOF</span></span>|<span data-ttu-id="1730f-115">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="1730f-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1730f-116">Namespace</span><span class="sxs-lookup"><span data-stu-id="1730f-116">Namespace</span></span>|<span data-ttu-id="1730f-117">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="1730f-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1730f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1730f-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
