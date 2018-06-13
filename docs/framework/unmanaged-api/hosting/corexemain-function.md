---
title: _CorExeMain 関数
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63af5979b113f81c01c9c68d6cccdfa10811265a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429135"
---
# <a name="corexemain-function"></a><span data-ttu-id="f157d-102">_CorExeMain 関数</span><span class="sxs-lookup"><span data-stu-id="f157d-102">_CorExeMain Function</span></span>
<span data-ttu-id="f157d-103">共通言語ランタイム (CLR) を初期化、実行可能アセンブリの CLR ヘッダーでマネージ エントリ ポイントを検索および実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="f157d-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f157d-104">構文</span><span class="sxs-lookup"><span data-stu-id="f157d-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f157d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="f157d-105">Remarks</span></span>  
 <span data-ttu-id="f157d-106">この関数は、マネージ実行可能アセンブリから作成されたプロセスにローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f157d-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="f157d-107">DLL アセンブリ ローダーの呼び出し、 [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="f157d-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="f157d-108">オペレーティング システム ローダーでは、イメージ ファイルに指定されたエントリ ポイントに関係なく、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f157d-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="f157d-109">Windows 98、Windows ME、Windows NT、および Windows 2000 で、`_CorExeMain`関数は、間接的に呼び出される、オペレーティング システム ローダーで fixup を通じてします。</span><span class="sxs-lookup"><span data-stu-id="f157d-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="f157d-110">その他のすべてのバージョンの Windows では、オペレーティング システム ローダーによって直接呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f157d-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="f157d-111">詳細については、「解説」セクションを参照してください、 [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="f157d-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f157d-112">要件</span><span class="sxs-lookup"><span data-stu-id="f157d-112">Requirements</span></span>  
 <span data-ttu-id="f157d-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f157d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f157d-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f157d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f157d-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f157d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f157d-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f157d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f157d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f157d-117">See Also</span></span>  
 [<span data-ttu-id="f157d-118">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="f157d-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
