---
title: _CorDllMain 関数
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d541f834e829305fa2b091c45d0dc8f387bb55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431671"
---
# <a name="cordllmain-function"></a><span data-ttu-id="2f273-102">_CorDllMain 関数</span><span class="sxs-lookup"><span data-stu-id="2f273-102">_CorDllMain Function</span></span>
<span data-ttu-id="2f273-103">共通言語ランタイム (CLR) を初期化、DLL アセンブリの CLR ヘッダーでマネージ エントリ ポイントを検索および実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="2f273-103">Initializes the common language runtime (CLR), locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f273-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f273-104">Syntax</span></span>  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f273-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f273-105">Parameters</span></span>  
 `hInst`  
 <span data-ttu-id="2f273-106">[in]読み込まれたモジュールのインスタンス ハンドル。</span><span class="sxs-lookup"><span data-stu-id="2f273-106">[in] The instance handle of the loaded module.</span></span>  
  
 `dwReason`  
 <span data-ttu-id="2f273-107">[in]DLL エントリ ポイント関数が呼び出される理由を示します。</span><span class="sxs-lookup"><span data-stu-id="2f273-107">[in]Indicates why the DLL entry-point function is being called.</span></span> <span data-ttu-id="2f273-108">このパラメーターは、次の値のいずれかを指定できます: DLL_PROCESS_ATTACH、DLL_THREAD_ATTACH、DLL_THREAD_ATTACH、またはあります。</span><span class="sxs-lookup"><span data-stu-id="2f273-108">This parameter can be one of the following values: DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH, DLL_THREAD_ATTACH, or DLL_PROCESS_DETACH.</span></span> <span data-ttu-id="2f273-109">これらの値の詳細については、次を参照してください。、`DllMain`プラットフォーム SDK のドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="2f273-109">For descriptions of these values, see the `DllMain` documentation in the Platform SDK.</span></span>  
  
 `lpReserved`  
 <span data-ttu-id="2f273-110">[in]使用しません。</span><span class="sxs-lookup"><span data-stu-id="2f273-110">[in] Unused.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f273-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="2f273-111">Return Value</span></span>  
 <span data-ttu-id="2f273-112">このメソッドが戻る`true`の成功と`false`場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2f273-112">This method returns `true` for success and `false` if an error occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f273-113">コメント</span><span class="sxs-lookup"><span data-stu-id="2f273-113">Remarks</span></span>  
 <span data-ttu-id="2f273-114">この関数は、DLL アセンブリのオペレーティング システム ローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2f273-114">This function is called by the operating system loader for DLL assemblies.</span></span> <span data-ttu-id="2f273-115">実行可能アセンブリ ローダーの呼び出し、 [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="2f273-115">For executable assemblies, the loader calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="2f273-116">オペレーティング システム ローダーでは、DLL のファイルで指定されたエントリ ポイントに関係なく、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2f273-116">The operating system loader calls this method regardless of the entry point specified in the DLL file.</span></span>  
  
 <span data-ttu-id="2f273-117">Windows 98、Windows ME、Windows NT、および Windows 2000 で、`_CorDllMain`関数が直接呼び出されていない、fixupin を介してオペレーティング システム ローダー。</span><span class="sxs-lookup"><span data-stu-id="2f273-117">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorDllMain` function is called indirectly through a fixupin the operating system loader.</span></span> <span data-ttu-id="2f273-118">その他のすべてのバージョンの Windows では、オペレーティング システム ローダーによって直接呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2f273-118">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="2f273-119">詳細については、「解説」セクションを参照してください、 [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="2f273-119">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f273-120">要件</span><span class="sxs-lookup"><span data-stu-id="2f273-120">Requirements</span></span>  
 <span data-ttu-id="2f273-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f273-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f273-122">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2f273-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f273-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="2f273-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f273-124">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f273-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f273-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f273-125">See Also</span></span>  
 [<span data-ttu-id="2f273-126">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="2f273-126">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
