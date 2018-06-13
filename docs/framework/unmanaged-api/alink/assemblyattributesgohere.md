---
title: AssemblyAttributesGoHere
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHere
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c24ca43f35e237b6387e108563b1f9c9ed432242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402396"
---
# <a name="assemblyattributesgohere"></a><span data-ttu-id="20259-102">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="20259-102">AssemblyAttributesGoHere</span></span>
<span data-ttu-id="20259-103">ALink でプレースホルダーとして使用し、カスタム属性に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="20259-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20259-104">構文</span><span class="sxs-lookup"><span data-stu-id="20259-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHere  
```  
  
## <a name="remarks"></a><span data-ttu-id="20259-105">コメント</span><span class="sxs-lookup"><span data-stu-id="20259-105">Remarks</span></span>  
 <span data-ttu-id="20259-106">この型への参照は、ソースにアセンブリのカスタム属性が含まれている netmodule 内部に埋め込まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="20259-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="20259-107">これらの型への参照が含まれる 1 つまたは複数の  netmodule からアセンブリ マニフェストを作成すると、ALink はこれらの参照にアタッチされた情報を使用して、実際のカスタム属性を生成します。</span><span class="sxs-lookup"><span data-stu-id="20259-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="20259-108">このため、この型がインスタンス化されることはなく、その型への参照はビルド処理の一部としてのみ使用され、最終的なアセンブリでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="20259-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="20259-109">この型への参照は、セキュリティに関連せず複数の用途を持たないカスタム属性を示します。</span><span class="sxs-lookup"><span data-stu-id="20259-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="20259-110">これらの型は .NET Framework 内で "内部的" とマーク付けされ、<xref:System.Runtime.CompilerServices> にあります。</span><span class="sxs-lookup"><span data-stu-id="20259-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20259-111">要件</span><span class="sxs-lookup"><span data-stu-id="20259-111">Requirements</span></span>  
 <span data-ttu-id="20259-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="20259-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20259-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="20259-113">See Also</span></span>  
 [<span data-ttu-id="20259-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="20259-114">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="20259-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="20259-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="20259-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="20259-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
