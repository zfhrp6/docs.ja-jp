---
title: "CorFieldAttr 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFieldAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFieldAttr
helpviewer_keywords: CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b199764ea0fb2d02b01d7cf04d1fa8fad743109f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="a2054-102">CorFieldAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="a2054-102">CorFieldAttr Enumeration</span></span>
<span data-ttu-id="a2054-103">フィールドについてのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a2054-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2054-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2054-104">Syntax</span></span>  
  
```  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a2054-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a2054-105">Members</span></span>  
  
|<span data-ttu-id="a2054-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a2054-106">Member</span></span>|<span data-ttu-id="a2054-107">説明</span><span class="sxs-lookup"><span data-stu-id="a2054-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="a2054-108">ユーザー補助に関する情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="a2054-109">フィールドを参照できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="a2054-110">フィールドが親の型からのみアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="a2054-111">フィールドにそれが属するアセンブリ内の派生クラスでアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="a2054-112">フィールドにそれが属するアセンブリ内のすべての型によってアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="a2054-113">フィールドがその型によってのみアクセスできますが、派生クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="a2054-114">フィールドがそのアセンブリ内のすべての型と派生クラスによってアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="a2054-115">フィールドにこのスコープの可視性を持つすべての型からアクセスできることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="a2054-116">フィールドがインスタンス メンバーではなく、その型のメンバーであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="a2054-117">初期化された後に、フィールドを変更できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="a2054-118">フィールドの値が、コンパイル時定数であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="a2054-119">その型は、リモート処理は実行時に、フィールドはシリアル化されませんを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="a2054-120">フィールドが、特別なことと、その名前が記述されているを指定する方法です。</span><span class="sxs-lookup"><span data-stu-id="a2054-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="a2054-121">PInvoke によってフィールドの実装が転送されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="a2054-122">共通言語ランタイムでは、内部使用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="a2054-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="a2054-123">共通言語ランタイム メタデータの内部 Api が名のエンコードを確認する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="a2054-124">フィールドにマーシャ リング情報が含まれることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="a2054-125">フィールドが既定値を持つことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="a2054-126">フィールドの相対仮想アドレスを持つことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2054-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2054-127">要件</span><span class="sxs-lookup"><span data-stu-id="a2054-127">Requirements</span></span>  
 <span data-ttu-id="a2054-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a2054-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2054-129">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a2054-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a2054-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2054-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2054-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2054-131">See Also</span></span>  
 [<span data-ttu-id="a2054-132">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="a2054-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
