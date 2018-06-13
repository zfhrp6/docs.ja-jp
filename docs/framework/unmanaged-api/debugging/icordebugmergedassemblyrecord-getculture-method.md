---
title: ICorDebugMergedAssemblyRecord::GetCulture メソッド
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f2336c89a32b202c4226f1ed194d786be6fa020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415358"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="9eef1-102">ICorDebugMergedAssemblyRecord::GetCulture メソッド</span><span class="sxs-lookup"><span data-stu-id="9eef1-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="9eef1-103">アセンブリのカルチャ名文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="9eef1-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eef1-104">構文</span><span class="sxs-lookup"><span data-stu-id="9eef1-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9eef1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9eef1-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="9eef1-106">[in] `szCulture` バッファー内の文字数。</span><span class="sxs-lookup"><span data-stu-id="9eef1-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="9eef1-107">[out] `szCulture` バッファーに実際に書き込まれた文字数。</span><span class="sxs-lookup"><span data-stu-id="9eef1-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="9eef1-108">[out] カルチャ名を格納する文字配列。</span><span class="sxs-lookup"><span data-stu-id="9eef1-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9eef1-109">コメント</span><span class="sxs-lookup"><span data-stu-id="9eef1-109">Remarks</span></span>  
 <span data-ttu-id="9eef1-110">カルチャ名は、"en-US" (英語 (米国) カルチャ)、"neutral" (ニュートラル カルチャ) など、カルチャを識別する一意の文字列です。</span><span class="sxs-lookup"><span data-stu-id="9eef1-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9eef1-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9eef1-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eef1-112">要件</span><span class="sxs-lookup"><span data-stu-id="9eef1-112">Requirements</span></span>  
 <span data-ttu-id="9eef1-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9eef1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eef1-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9eef1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eef1-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eef1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eef1-116">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eef1-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eef1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9eef1-117">See Also</span></span>  
 [<span data-ttu-id="9eef1-118">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9eef1-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="9eef1-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9eef1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
