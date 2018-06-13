---
title: CoreClrDebugRuntimeInfo 構造体
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88fcc5959054f1cdf7c9543674584a4bde26d896
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402071"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="cb04b-102">CoreClrDebugRuntimeInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="cb04b-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="cb04b-103">リモート コンピューター上のプロセスに読み込まれる共通言語ランタイム (CLR) インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="cb04b-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb04b-104">構文</span><span class="sxs-lookup"><span data-stu-id="cb04b-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="cb04b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb04b-105">Members</span></span>  
  
|<span data-ttu-id="cb04b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="cb04b-106">Member</span></span>|<span data-ttu-id="cb04b-107">説明</span><span class="sxs-lookup"><span data-stu-id="cb04b-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="cb04b-108">対象のコンピューターで実行されているリモート デバッグ プロキシによって割り当てられたランタイム識別子。</span><span class="sxs-lookup"><span data-stu-id="cb04b-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb04b-109">要件</span><span class="sxs-lookup"><span data-stu-id="cb04b-109">Requirements</span></span>  
 <span data-ttu-id="cb04b-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cb04b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb04b-111">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="cb04b-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="cb04b-112">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="cb04b-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="cb04b-113">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="cb04b-113">**.NET Framework Versions:** 3.5 SP1</span></span>
