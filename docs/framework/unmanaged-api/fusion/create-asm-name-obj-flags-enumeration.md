---
title: "CREATE_ASM_NAME_OBJ_FLAGS 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CREATE_ASM_NAME_OBJ_FLAGS
api_location: fusion.dll
api_type: COM
f1_keywords: CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords: CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4982b33643d855be4b8cace59f1c5cac4201d5ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="createasmnameobjflags-enumeration"></a><span data-ttu-id="b44c3-102">CREATE_ASM_NAME_OBJ_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="b44c3-102">CREATE_ASM_NAME_OBJ_FLAGS Enumeration</span></span>
<span data-ttu-id="b44c3-103">属性を指定、 [IAssemblyName インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)オブジェクトで構築したとき、 [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)関数。</span><span class="sxs-lookup"><span data-stu-id="b44c3-103">Specifies the attributes of an [IAssemblyName Interface](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object when it is constructed by the [CreateAssemblyNameObject](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b44c3-104">構文</span><span class="sxs-lookup"><span data-stu-id="b44c3-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =   
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="b44c3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b44c3-105">Members</span></span>  
  
|<span data-ttu-id="b44c3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b44c3-106">Member</span></span>|<span data-ttu-id="b44c3-107">説明</span><span class="sxs-lookup"><span data-stu-id="b44c3-107">Description</span></span>|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|<span data-ttu-id="b44c3-108">渡されたパラメーターが、テキスト id であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b44c3-108">Indicates that the parameter passed is a textual identity.</span></span>|  
|`CANOF_SET_DEFAULT_VALUES`|<span data-ttu-id="b44c3-109">いくつかの既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b44c3-109">Sets a few default values.</span></span>|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|<span data-ttu-id="b44c3-110">フレンド アセンブリのルール (名前と公開キーのみ) を確認します。</span><span class="sxs-lookup"><span data-stu-id="b44c3-110">Verifies the friend assembly rule (only name and public key).</span></span> <span data-ttu-id="b44c3-111">このメンバーは、内部使用のみです。</span><span class="sxs-lookup"><span data-stu-id="b44c3-111">This member is for internal use only.</span></span>|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|<span data-ttu-id="b44c3-112">組み合わせ、`CANOF_PARSE_DISPLAY_NAME`と`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`フラグ。</span><span class="sxs-lookup"><span data-stu-id="b44c3-112">A combination of the `CANOF_PARSE_DISPLAY_NAME` and `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` flags.</span></span> <span data-ttu-id="b44c3-113">このメンバーは、内部使用のみです。</span><span class="sxs-lookup"><span data-stu-id="b44c3-113">This member is for internal use only.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b44c3-114">要件</span><span class="sxs-lookup"><span data-stu-id="b44c3-114">Requirements</span></span>  
 <span data-ttu-id="b44c3-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b44c3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b44c3-116">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b44c3-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b44c3-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b44c3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44c3-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b44c3-118">See Also</span></span>  
 [<span data-ttu-id="b44c3-119">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b44c3-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="b44c3-120">CreateAssemblyNameObject 関数</span><span class="sxs-lookup"><span data-stu-id="b44c3-120">CreateAssemblyNameObject Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 [<span data-ttu-id="b44c3-121">Fusion 列挙体</span><span class="sxs-lookup"><span data-stu-id="b44c3-121">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
