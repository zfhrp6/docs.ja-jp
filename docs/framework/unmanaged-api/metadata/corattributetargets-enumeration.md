---
title: CorAttributeTargets 列挙型
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d239c3091b29424b26fbab4cb4eb9152ff9ad9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442167"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="72c83-102">CorAttributeTargets 列挙型</span><span class="sxs-lookup"><span data-stu-id="72c83-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="72c83-103">属性を適用できるアプリケーション要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="72c83-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72c83-104">構文</span><span class="sxs-lookup"><span data-stu-id="72c83-104">Syntax</span></span>  
  
```  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =   
        catAssembly | catModule | catClass | catStruct |   
        catEnum | catConstructor | catMethod | catProperty |   
        catField | catEvent | catInterface | catParameter |   
        catDelegate | catGenericParameter,  
  
    catClassMembers        =   
        catClass | catStruct | catEnum | catConstructor |   
        catMethod | catProperty | catField | catEvent |   
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="72c83-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="72c83-105">Members</span></span>  
  
|<span data-ttu-id="72c83-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="72c83-106">Member</span></span>|<span data-ttu-id="72c83-107">説明</span><span class="sxs-lookup"><span data-stu-id="72c83-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="72c83-108">属性は、アセンブリに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="72c83-109">属性は、ポータブル実行可能ファイル (.dll または .exe) モジュールに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="72c83-110">属性は、クラスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="72c83-111">属性は、構造体に適用できます。つまり、値を入力します。</span><span class="sxs-lookup"><span data-stu-id="72c83-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="72c83-112">属性は、列挙体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="72c83-113">属性は、コンス トラクターに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="72c83-114">属性は、メソッドに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="72c83-115">属性は、プロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="72c83-116">属性は、フィールドに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="72c83-117">属性は、イベントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="72c83-118">属性は、インターフェイスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="72c83-119">属性は、パラメーターに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="72c83-120">属性は、デリゲートに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="72c83-121">属性は、ジェネリック パラメーターに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="72c83-122">属性は、任意のアプリケーション要素に適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="72c83-123">属性は、クラスのメンバーに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72c83-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72c83-124">コメント</span><span class="sxs-lookup"><span data-stu-id="72c83-124">Remarks</span></span>  
 <span data-ttu-id="72c83-125">`CorAttributeTargets`列挙値は、優先の組み合わせを取得するビットごとの OR 演算と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="72c83-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="72c83-126">`CorAttributeTargets`は対応しているマネージ<xref:System.AttributeTargets?displayProperty=nameWithType>列挙します。</span><span class="sxs-lookup"><span data-stu-id="72c83-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72c83-127">要件</span><span class="sxs-lookup"><span data-stu-id="72c83-127">Requirements</span></span>  
 <span data-ttu-id="72c83-128">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="72c83-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72c83-129">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="72c83-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="72c83-130">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72c83-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72c83-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="72c83-131">See Also</span></span>  
 [<span data-ttu-id="72c83-132">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="72c83-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
