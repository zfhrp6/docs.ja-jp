---
title: "SetManifestFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink3.SetManifestFile
api_location: alink.dll
api_type: COM
f1_keywords: SetManifestFile
helpviewer_keywords: SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 807452326193d193f3bc603ebc7b74a5a0f1c281
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="a54f6-102">SetManifestFile メソッド</span><span class="sxs-lookup"><span data-stu-id="a54f6-102">SetManifestFile Method</span></span>
<span data-ttu-id="a54f6-103">指定するか、アセンブリの作成時に、リンカーが使用するマニフェスト ファイルをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="a54f6-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a54f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="a54f6-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a54f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a54f6-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="a54f6-106">内容が Win32 リソースの blob に格納するマニフェスト ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="a54f6-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a54f6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a54f6-107">Return Value</span></span>  
 <span data-ttu-id="a54f6-108">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="a54f6-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a54f6-109">コメント</span><span class="sxs-lookup"><span data-stu-id="a54f6-109">Remarks</span></span>  
 <span data-ttu-id="a54f6-110">これを呼び出して、Win32ResBlob を求めます。</span><span class="sxs-lookup"><span data-stu-id="a54f6-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="a54f6-111">値、`pszFile`パラメーターは、その内容の読み取りおよび RT_MANIFEST の ID では、Win32 リソースにマニフェスト ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="a54f6-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="a54f6-112">NULL のパラメーターを使用して呼び出されると、以前に読み取られたマニフェストがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="a54f6-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="a54f6-113">これにより、1 つの初期化時に、リンカーの状態をリセットすることができます。</span><span class="sxs-lookup"><span data-stu-id="a54f6-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a54f6-114">要件</span><span class="sxs-lookup"><span data-stu-id="a54f6-114">Requirements</span></span>  
 <span data-ttu-id="a54f6-115">ALink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="a54f6-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a54f6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="a54f6-116">See Also</span></span>  
 [<span data-ttu-id="a54f6-117">IALink3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a54f6-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [<span data-ttu-id="a54f6-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="a54f6-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="a54f6-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a54f6-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a54f6-120">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="a54f6-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
