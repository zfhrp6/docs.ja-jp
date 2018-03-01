---
title: AssemblyAttributesGoHereS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- AssemblyAttributesGoHereS
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ac8f25632521f2e8abe5209608e42632293feb4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgoheres"></a><span data-ttu-id="8836b-102">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="8836b-102">AssemblyAttributesGoHereS</span></span>
<span data-ttu-id="8836b-103">ALink でプレースホルダーとして使用し、カスタム属性に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="8836b-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8836b-104">構文</span><span class="sxs-lookup"><span data-stu-id="8836b-104">Syntax</span></span>  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a><span data-ttu-id="8836b-105">コメント</span><span class="sxs-lookup"><span data-stu-id="8836b-105">Remarks</span></span>  
 <span data-ttu-id="8836b-106">この型への参照は、ソースにアセンブリのカスタム属性が含まれている netmodule 内部に埋め込まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="8836b-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="8836b-107">これらの型への参照が含まれる 1 つまたは複数の  netmodule からアセンブリ マニフェストを作成すると、ALink はこれらの参照にアタッチされた情報を使用して、実際のカスタム属性を生成します。</span><span class="sxs-lookup"><span data-stu-id="8836b-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="8836b-108">このため、この型がインスタンス化されることはなく、その型への参照はビルド処理の一部としてのみ使用され、最終的なアセンブリでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="8836b-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>  
  
 <span data-ttu-id="8836b-109">この型への参照は、セキュリティに関連せず複数の用途を持たないカスタム属性を示します。</span><span class="sxs-lookup"><span data-stu-id="8836b-109">References to this type indicate custom attributes that are security related and are not multiple-use.</span></span>  
  
 <span data-ttu-id="8836b-110">これらの型は .NET Framework 内で "内部的" とマーク付けされ、<xref:System.Runtime.CompilerServices> にあります。</span><span class="sxs-lookup"><span data-stu-id="8836b-110">These types are marked "internal" within the .NET Framework, and are located in <xref:System.Runtime.CompilerServices>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8836b-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="8836b-111">Requirements</span></span>  
 <span data-ttu-id="8836b-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="8836b-112">mscorlib.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8836b-113">参照</span><span class="sxs-lookup"><span data-stu-id="8836b-113">See Also</span></span>  
 [<span data-ttu-id="8836b-114">AssemblyAttributesGoHere</span><span class="sxs-lookup"><span data-stu-id="8836b-114">AssemblyAttributesGoHere</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [<span data-ttu-id="8836b-115">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="8836b-115">AssemblyAttributesGoHereM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [<span data-ttu-id="8836b-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="8836b-116">AssemblyAttributesGoHereSM</span></span>](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
