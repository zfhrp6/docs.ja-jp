---
title: "IValidator::FormatEventInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0775bf5a2370d9d05899af5bc414caf08b3401fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="47203-102">IValidator::FormatEventInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="47203-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="47203-103">指定された検証エラーに対応するエラー メッセージを取得します。</span><span class="sxs-lookup"><span data-stu-id="47203-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47203-104">構文</span><span class="sxs-lookup"><span data-stu-id="47203-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47203-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47203-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="47203-106">[in]検証のエラー ハンドラーに渡された HRESULT 値。</span><span class="sxs-lookup"><span data-stu-id="47203-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="47203-107">[in]A`VEContext`検証エラーに関するコンテキスト情報を格納しているインスタンス。</span><span class="sxs-lookup"><span data-stu-id="47203-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="47203-108">[入力、出力].返されたエラー メッセージを含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="47203-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="47203-109">[in]エラー メッセージの最大長。</span><span class="sxs-lookup"><span data-stu-id="47203-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="47203-110">[in]エラーを説明する追加のパラメーターを格納するセーフである配列。</span><span class="sxs-lookup"><span data-stu-id="47203-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47203-111">要件</span><span class="sxs-lookup"><span data-stu-id="47203-111">Requirements</span></span>  
 <span data-ttu-id="47203-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="47203-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47203-113">**ヘッダー:** IValidator.idl、IValidator.h</span><span class="sxs-lookup"><span data-stu-id="47203-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="47203-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="47203-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47203-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47203-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47203-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="47203-116">See Also</span></span>  
 
