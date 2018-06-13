---
title: ICLRDataTarget2::FreeVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7351dfb046653e4f3e20e0dc8a4bba8653ec36e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404649"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="4a70d-102">ICLRDataTarget2::FreeVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="4a70d-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="4a70d-103">ターゲット プロセスのアドレス空間に割り当てられていたメモリを解放共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4a70d-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a70d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4a70d-104">Syntax</span></span>  
  
```  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a70d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4a70d-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="4a70d-106">[in]A`CLRDATA_ADDRESS`解放されるメモリの開始アドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="4a70d-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="4a70d-107">[in]解放するメモリのバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="4a70d-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="4a70d-108">[in]メモリの解放を制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="4a70d-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="4a70d-109">Win32 を参照してください`VirtualFree`関数。</span><span class="sxs-lookup"><span data-stu-id="4a70d-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a70d-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4a70d-110">Remarks</span></span>  
 <span data-ttu-id="4a70d-111">`FreeVirtual`メソッドは、Win32 の論理ラッパーとして機能`VirtualFree`関数。</span><span class="sxs-lookup"><span data-stu-id="4a70d-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="4a70d-112">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="4a70d-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a70d-113">要件</span><span class="sxs-lookup"><span data-stu-id="4a70d-113">Requirements</span></span>  
 <span data-ttu-id="4a70d-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4a70d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a70d-115">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4a70d-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4a70d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a70d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a70d-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a70d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a70d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a70d-118">See Also</span></span>  
 [<span data-ttu-id="4a70d-119">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a70d-119">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="4a70d-120">AllocVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="4a70d-120">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)
