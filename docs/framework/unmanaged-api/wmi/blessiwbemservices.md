---
title: "BlessIWbemServices 関数 (アンマネージ API リファレンス)"
description: "BlessIWbemServices 関数では、ユーザーの資格情報が IWbemServices クラスへのアクセスを許可するかどうかを示します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BlessIWbemServices
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BlessIWbemServices
helpviewer_keywords: BlessIWbemServices function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f384e8d045dd7a6f2f864f0991f8caf4a674408b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="5e801-103">BlessIWbemServices 関数</span><span class="sxs-lookup"><span data-stu-id="5e801-103">BlessIWbemServices function</span></span>
<span data-ttu-id="5e801-104">ユーザーの資格情報が、指定したへのアクセスを許可するかどうかを示す[IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)クラスです。</span><span class="sxs-lookup"><span data-stu-id="5e801-104">Indicates whether the user credentials permit access to the specified [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) class.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5e801-105">構文</span><span class="sxs-lookup"><span data-stu-id="5e801-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="5e801-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e801-106">Parameters</span></span>

`pIWbemServices`  
<span data-ttu-id="5e801-107">[in]ポインター、 [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx)オブジェクトのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="5e801-107">[in] A pointer to the [IWbemServices](https://msdn.microsoft.com/library/aa392093(v=vs.85).aspx) object for which permissions are required.</span></span>

`strUser`  
<span data-ttu-id="5e801-108">[in]ユーザー名。</span><span class="sxs-lookup"><span data-stu-id="5e801-108">[in] The user name.</span></span>

`strPassword`  
<span data-ttu-id="5e801-109">[in]関連付けられているパスワード`strUser`です。</span><span class="sxs-lookup"><span data-stu-id="5e801-109">[in] The password associated with `strUser`.</span></span>

<span data-ttu-id="5e801-110">`strAuthority`[in]ユーザーのドメイン名。</span><span class="sxs-lookup"><span data-stu-id="5e801-110">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="5e801-111">参照してください、 [ConnectServerWmi](connectserverwmi.md)関数の詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="5e801-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="5e801-112">`impLevel`[in]権限借用レベルです。</span><span class="sxs-lookup"><span data-stu-id="5e801-112">`impLevel` [in] The impersonation level.</span></span>

<span data-ttu-id="5e801-113">`authnLevel`[in]承認レベル。</span><span class="sxs-lookup"><span data-stu-id="5e801-113">`authnLevel` [in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="5e801-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="5e801-114">Return value</span></span>

<span data-ttu-id="5e801-115">この関数によって返される次の値が定義されている、 *WinError.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="5e801-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5e801-116">定数</span><span class="sxs-lookup"><span data-stu-id="5e801-116">Constant</span></span>  |<span data-ttu-id="5e801-117">[値]</span><span class="sxs-lookup"><span data-stu-id="5e801-117">Value</span></span>  |<span data-ttu-id="5e801-118">説明</span><span class="sxs-lookup"><span data-stu-id="5e801-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="5e801-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="5e801-119">0x80070057</span></span> | <span data-ttu-id="5e801-120">1 つまたは複数の引数が無効です。</span><span class="sxs-lookup"><span data-stu-id="5e801-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="5e801-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="5e801-121">0x80004003</span></span> | <span data-ttu-id="5e801-122">`pIWbemServices` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="5e801-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="5e801-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="5e801-123">0x80000008</span></span> | <span data-ttu-id="5e801-124">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5e801-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="5e801-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="5e801-125">0x80000002</span></span> | <span data-ttu-id="5e801-126">操作の実行に使用できるは、メモリ不足です。</span><span class="sxs-lookup"><span data-stu-id="5e801-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="5e801-127">0</span><span class="sxs-lookup"><span data-stu-id="5e801-127">0</span></span> | <span data-ttu-id="5e801-128">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="5e801-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="5e801-129">必要条件</span><span class="sxs-lookup"><span data-stu-id="5e801-129">Requirements</span></span>  
 <span data-ttu-id="5e801-130">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5e801-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e801-131">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5e801-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5e801-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e801-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e801-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e801-133">See also</span></span>  
[<span data-ttu-id="5e801-134">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="5e801-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
