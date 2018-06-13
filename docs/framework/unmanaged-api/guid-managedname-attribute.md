---
title: GUID_ManagedName 属性
ms.date: 03/30/2017
api_name:
- GUID_ManagedName
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GUID_ManagedName
helpviewer_keywords:
- GUID_ManagedName attribute
ms.assetid: 11e18095-e444-47bc-aff6-b887ac5dc01e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bae50f695de81856d4fddcb2af3d1188d896642
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430012"
---
# <a name="guidmanagedname-attribute"></a><span data-ttu-id="7d665-102">GUID_ManagedName 属性</span><span class="sxs-lookup"><span data-stu-id="7d665-102">GUID_ManagedName Attribute</span></span>
<span data-ttu-id="7d665-103">コンポーネント オブジェクト モデル (COM) ライブラリの管理対象名前空間名を指定するカスタム インターフェイス属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="7d665-103">Defines a custom interface attribute that specifies the managed namespace name for a component object model (COM) library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d665-104">構文</span><span class="sxs-lookup"><span data-stu-id="7d665-104">Syntax</span></span>  
  
```  
[  
   custom(GUID_ManagedName, value)  
]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d665-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7d665-105">Parameters</span></span>  
 `value`  
 <span data-ttu-id="7d665-106">ライブラリの管理対象名前空間の名前。</span><span class="sxs-lookup"><span data-stu-id="7d665-106">The managed namespace name for the library.</span></span>  
  
## <a name="definition"></a><span data-ttu-id="7d665-107">定義</span><span class="sxs-lookup"><span data-stu-id="7d665-107">Definition</span></span>  
 <span data-ttu-id="7d665-108">`GUID_ManagedName` 次の定義 Cor.h で。</span><span class="sxs-lookup"><span data-stu-id="7d665-108">`GUID_ManagedName` is defined in Cor.h as follows:</span></span>  
  
```  
// {0F21F359-AB84-41e8-9A78-36D110E6D2F9}  
EXTERN_GUID(GUID_ManagedName, 0xf21f359, 0xab84, 0x41e8, 0x9a, 0x78, 0x36, 0xd1, 0x10, 0xe6, 0xd2, 0xf9);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7d665-109">コメント</span><span class="sxs-lookup"><span data-stu-id="7d665-109">Remarks</span></span>  
 <span data-ttu-id="7d665-110">カスタム インターフェイス属性は、タイプ ライブラリのオブジェクトのメタデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="7d665-110">A custom interface attribute defines metadata for an object in the type library.</span></span>  
  
 <span data-ttu-id="7d665-111">使用して<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType>または<xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType>属性から管理対象の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="7d665-111">Use <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetCustData%2A?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.ComTypes.ITypeLib2.GetCustData%2A?displayProperty=nameWithType> to retrieve the managed name from the attribute.</span></span>  
  
 <span data-ttu-id="7d665-112">詳細については、次を参照してください。[インターフェイス属性](/cpp/windows/interface-attributes)Visual c のドキュメントを参照しています。</span><span class="sxs-lookup"><span data-stu-id="7d665-112">For more information, see [Interface Attributes](/cpp/windows/interface-attributes) in the Visual C++ reference documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d665-113">例</span><span class="sxs-lookup"><span data-stu-id="7d665-113">Example</span></span>  
 <span data-ttu-id="7d665-114">次の例を使用してライブラリの定義、`GUID_ManagedName`属性。</span><span class="sxs-lookup"><span data-stu-id="7d665-114">The following example shows a library definition using the `GUID_ManagedName` attribute.</span></span>  
  
```  
[  
   ...  
   custom(GUID_ManagedName, Microsoft.VisualStudio.CommandBars.dll")  
]  
library Microsoft_VisualStudio_CommandBars  
{  
   ...  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="7d665-115">要件</span><span class="sxs-lookup"><span data-stu-id="7d665-115">Requirements</span></span>  
 <span data-ttu-id="7d665-116">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7d665-116">**Header:** Cor.h</span></span>
