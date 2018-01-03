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
ms.workload: dotnet
ms.openlocfilehash: cf48153454fbb2c24dc3f1cfe1f82deefa4ee723
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="6f36e-102">SetManifestFile メソッド</span><span class="sxs-lookup"><span data-stu-id="6f36e-102">SetManifestFile Method</span></span>
<span data-ttu-id="6f36e-103">指定するか、アセンブリの作成時に、リンカーが使用するマニフェスト ファイルをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="6f36e-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f36e-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f36e-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f36e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f36e-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="6f36e-106">内容が Win32 リソースの blob に格納するマニフェスト ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="6f36e-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f36e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="6f36e-107">Return Value</span></span>  
 <span data-ttu-id="6f36e-108">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="6f36e-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f36e-109">コメント</span><span class="sxs-lookup"><span data-stu-id="6f36e-109">Remarks</span></span>  
 <span data-ttu-id="6f36e-110">これを呼び出して、Win32ResBlob を求めます。</span><span class="sxs-lookup"><span data-stu-id="6f36e-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="6f36e-111">値、`pszFile`パラメーターは、その内容の読み取りおよび RT_MANIFEST の ID では、Win32 リソースにマニフェスト ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="6f36e-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="6f36e-112">NULL のパラメーターを使用して呼び出されると、以前に読み取られたマニフェストがクリアされます。</span><span class="sxs-lookup"><span data-stu-id="6f36e-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="6f36e-113">これにより、1 つの初期化時に、リンカーの状態をリセットすることができます。</span><span class="sxs-lookup"><span data-stu-id="6f36e-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f36e-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="6f36e-114">Requirements</span></span>  
 <span data-ttu-id="6f36e-115">ALink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="6f36e-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f36e-116">参照</span><span class="sxs-lookup"><span data-stu-id="6f36e-116">See Also</span></span>  
 [<span data-ttu-id="6f36e-117">IALink3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f36e-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [<span data-ttu-id="6f36e-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="6f36e-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [<span data-ttu-id="6f36e-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f36e-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6f36e-120">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="6f36e-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
