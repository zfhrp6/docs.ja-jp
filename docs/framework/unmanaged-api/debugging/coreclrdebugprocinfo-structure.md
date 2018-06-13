---
title: CoreClrDebugProcInfo 構造体
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9d4b27ca0bf454b42f15b849008e5a3019bb09a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402192"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="0c6da-102">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="0c6da-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="0c6da-103">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="0c6da-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c6da-104">構文</span><span class="sxs-lookup"><span data-stu-id="0c6da-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="0c6da-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="0c6da-105">Members</span></span>  
  
|<span data-ttu-id="0c6da-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="0c6da-106">Member</span></span>|<span data-ttu-id="0c6da-107">説明</span><span class="sxs-lookup"><span data-stu-id="0c6da-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="0c6da-108">OS によって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="0c6da-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="0c6da-109">対象のコンピューターで実行されているリモート デバッグ プロキシによって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="0c6da-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="0c6da-110">この識別子は OS 識別子よりも少ない頻度で再利用されます。</span><span class="sxs-lookup"><span data-stu-id="0c6da-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="0c6da-111">プロセスのコマンド ライン。</span><span class="sxs-lookup"><span data-stu-id="0c6da-111">Command-line of the process.</span></span> <span data-ttu-id="0c6da-112">このメンバーは切り詰められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0c6da-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c6da-113">要件</span><span class="sxs-lookup"><span data-stu-id="0c6da-113">Requirements</span></span>  
 <span data-ttu-id="0c6da-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0c6da-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c6da-115">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="0c6da-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="0c6da-116">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="0c6da-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="0c6da-117">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="0c6da-117">**.NET Framework Versions:** 3.5 SP1</span></span>
