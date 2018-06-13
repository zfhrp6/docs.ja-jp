---
title: AssemblyAttributesGoHereM
ms.date: 03/30/2017
api_name:
- AssemblyAttributesGoHereM
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereM
helpviewer_keywords:
- AssemblyAttributesGoHereM type
- Alink API, AssemblyAttributesGoHereM type
ms.assetid: caaa8ba9-b4bb-4dd6-934d-57e436b2f3e5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 075f0ce7001573bb4e61a3e059e699d15275ea0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403189"
---
# <a name="assemblyattributesgoherem"></a><span data-ttu-id="9d0a9-102">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="9d0a9-102">AssemblyAttributesGoHereM</span></span>
<span data-ttu-id="9d0a9-103">ALink でプレースホルダーとして使用し、カスタム属性に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="9d0a9-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0a9-104">構文</span><span class="sxs-lookup"><span data-stu-id="9d0a9-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereM  
```  
  
## <a name="remarks"></a><span data-ttu-id="9d0a9-105">コメント</span><span class="sxs-lookup"><span data-stu-id="9d0a9-105">Remarks</span></span>  
 <span data-ttu-id="9d0a9-106">この型への参照は、ソースにアセンブリのカスタム属性が含まれている netmodule 内部に埋め込まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="9d0a9-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="9d0a9-107">これらの型への参照が含まれる 1 つまたは複数の  netmodule からアセンブリ マニフェストを作成すると、ALink はこれらの参照にアタッチされた情報を使用して、実際のカスタム属性を生成します。</span><span class="sxs-lookup"><span data-stu-id="9d0a9-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="9d0a9-108">このため、この型がインスタンス化されることはなく、その型への参照はビルド処理の一部としてのみ使用され、最終的なアセンブリでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="9d0a9-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="9d0a9-109">この型への参照は、セキュリティに関連せず複数の用途を持つカスタム属性を示します。</span><span class="sxs-lookup"><span data-stu-id="9d0a9-109">References to this type indicate custom attributes that are not security related but are multiple-use.</span></span>  
  
 <span data-ttu-id="9d0a9-110">これらの型は .NET Framework 内で "内部的" とマーク付けされ、<xref:System.Runtime.CompilerServices> にあります。</span><span class="sxs-lookup"><span data-stu-id="9d0a9-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d0a9-111">要件</span><span class="sxs-lookup"><span data-stu-id="9d0a9-111">Requirements</span></span>  
 <span data-ttu-id="9d0a9-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="9d0a9-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0a9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d0a9-113">See Also</span></span>  
 [<span data-ttu-id="9d0a9-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="9d0a9-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="9d0a9-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="9d0a9-115">AssemblyAttributesGoHereS</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheres.md)  
 [<span data-ttu-id="9d0a9-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="9d0a9-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
