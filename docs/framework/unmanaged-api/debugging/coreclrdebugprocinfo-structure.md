---
title: "CoreClrDebugProcInfo 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoreClrDebugProcInfo
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53616fb8e947d2a301dcfcb4e3870a9a9dc36ec1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="ce4cd-102">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="ce4cd-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="ce4cd-103">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="ce4cd-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce4cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce4cd-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="ce4cd-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ce4cd-105">Members</span></span>  
  
|<span data-ttu-id="ce4cd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ce4cd-106">Member</span></span>|<span data-ttu-id="ce4cd-107">説明</span><span class="sxs-lookup"><span data-stu-id="ce4cd-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="ce4cd-108">OS によって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="ce4cd-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="ce4cd-109">対象のコンピューターで実行されているリモート デバッグ プロキシによって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="ce4cd-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="ce4cd-110">この識別子は OS 識別子よりも少ない頻度で再利用されます。</span><span class="sxs-lookup"><span data-stu-id="ce4cd-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="ce4cd-111">プロセスのコマンド ライン。</span><span class="sxs-lookup"><span data-stu-id="ce4cd-111">Command-line of the process.</span></span> <span data-ttu-id="ce4cd-112">このメンバーは切り詰められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ce4cd-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce4cd-113">要件</span><span class="sxs-lookup"><span data-stu-id="ce4cd-113">Requirements</span></span>  
 <span data-ttu-id="ce4cd-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ce4cd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce4cd-115">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="ce4cd-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ce4cd-116">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="ce4cd-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ce4cd-117">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ce4cd-117">**.NET Framework Versions:** 3.5 SP1</span></span>
