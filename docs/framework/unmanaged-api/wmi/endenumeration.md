---
title: "EndEnumeration 関数 (アンマネージ API リファレンス)"
description: "EndEnumeration 関数は、列挙を終了します。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndEnumeration
helpviewer_keywords:
- EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fee3137dad3f89fa8849b28e9ca38b40040f916e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endenumeration-function"></a><span data-ttu-id="572af-103">EndEnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="572af-103">EndEnumeration function</span></span>
<span data-ttu-id="572af-104">呼び出し時に起動列挙のシーケンスの終了、 [BeginEnumeration 関数](beginenumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="572af-104">Terminates an enumeration sequence started with a call to the [BeginEnumeration function](beginenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="572af-105">構文</span><span class="sxs-lookup"><span data-stu-id="572af-105">Syntax</span></span>  
  
```  
HRESULT EndEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="572af-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="572af-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="572af-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="572af-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="572af-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="572af-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>


## <a name="return-value"></a><span data-ttu-id="572af-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="572af-109">Return value</span></span>

<span data-ttu-id="572af-110">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="572af-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="572af-111">定数</span><span class="sxs-lookup"><span data-stu-id="572af-111">Constant</span></span>  |<span data-ttu-id="572af-112">[値]</span><span class="sxs-lookup"><span data-stu-id="572af-112">Value</span></span>  |<span data-ttu-id="572af-113">説明</span><span class="sxs-lookup"><span data-stu-id="572af-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="572af-114">0x80041001</span><span class="sxs-lookup"><span data-stu-id="572af-114">0x80041001</span></span> | <span data-ttu-id="572af-115">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="572af-115">There has been a general failure.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="572af-116">0</span><span class="sxs-lookup"><span data-stu-id="572af-116">0</span></span> | <span data-ttu-id="572af-117">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="572af-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="572af-118">コメント</span><span class="sxs-lookup"><span data-stu-id="572af-118">Remarks</span></span>

<span data-ttu-id="572af-119">この関数への呼び出しをラップする、 [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="572af-119">This function wraps a call to the [IWbemClassObject::EndEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) method.</span></span>

<span data-ttu-id="572af-120">呼び出し、`EndEnumeration`関数は必要ありませんが、列挙体に関連付けられているリソースを解放するためお勧めします。</span><span class="sxs-lookup"><span data-stu-id="572af-120">A call to the `EndEnumeration` function is not required, but it is recommended because it releases resources associated with the enumeration.</span></span> <span data-ttu-id="572af-121">ただし、resoruces は次回の列挙が開始されたか、オブジェクトが解放されるときに、自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="572af-121">However, the resoruces are deallocated automatically when the next enumeration is started or the object is released.</span></span>

## <a name="requirements"></a><span data-ttu-id="572af-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="572af-122">Requirements</span></span>  
 <span data-ttu-id="572af-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="572af-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="572af-124">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="572af-124">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="572af-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="572af-125">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572af-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="572af-126">See also</span></span>  
[<span data-ttu-id="572af-127">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="572af-127">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
