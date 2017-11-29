---
title: "BeginMethodEnumeration 関数 (アンマネージ API リファレンス)"
description: "オブジェクトのメソッドの列挙を開始する BeginMethodEnumeration 関数"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginMethodEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginMethodEnumeration
helpviewer_keywords: BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e44c432f9503f96ad4dab9e25b78e6dd148f94c
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2017
---
# <a name="beginenumeration-function"></a><span data-ttu-id="2434a-103">BeginEnumeration 関数</span><span class="sxs-lookup"><span data-stu-id="2434a-103">BeginEnumeration function</span></span>
<span data-ttu-id="2434a-104">オブジェクトの使用可能なメソッドの列挙を開始します。</span><span class="sxs-lookup"><span data-stu-id="2434a-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="2434a-105">構文</span><span class="sxs-lookup"><span data-stu-id="2434a-105">Syntax</span></span>  
  
``` 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="2434a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2434a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2434a-107">[in]このパラメーターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="2434a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2434a-108">[in]ポインター、 [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="2434a-108">[in] A pointer to an [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="2434a-109">[in]ゼロ (0) のすべてのメソッド、または列挙体のスコープを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="2434a-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="2434a-110">次のフラグが定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="2434a-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="2434a-111">定数</span><span class="sxs-lookup"><span data-stu-id="2434a-111">Constant</span></span>  |<span data-ttu-id="2434a-112">値</span><span class="sxs-lookup"><span data-stu-id="2434a-112">Value</span></span>  |<span data-ttu-id="2434a-113">説明</span><span class="sxs-lookup"><span data-stu-id="2434a-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="2434a-114">0x10</span><span class="sxs-lookup"><span data-stu-id="2434a-114">0x10</span></span> | <span data-ttu-id="2434a-115">列挙型クラス自体で定義されているメソッドを制限します。</span><span class="sxs-lookup"><span data-stu-id="2434a-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="2434a-116">0x20</span><span class="sxs-lookup"><span data-stu-id="2434a-116">0x20</span></span> | <span data-ttu-id="2434a-117">基本クラスから継承されたプロパティ、列挙型を制限します。</span><span class="sxs-lookup"><span data-stu-id="2434a-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="2434a-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="2434a-118">Return value</span></span>

<span data-ttu-id="2434a-119">この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定義する定数として、コード。</span><span class="sxs-lookup"><span data-stu-id="2434a-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2434a-120">定数</span><span class="sxs-lookup"><span data-stu-id="2434a-120">Constant</span></span>  |<span data-ttu-id="2434a-121">値</span><span class="sxs-lookup"><span data-stu-id="2434a-121">Value</span></span>  |<span data-ttu-id="2434a-122">説明</span><span class="sxs-lookup"><span data-stu-id="2434a-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2434a-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2434a-123">0x80041008</span></span> | <span data-ttu-id="2434a-124">`lEnnumFlags`ゼロ以外は、指定したフラグのいずれか。</span><span class="sxs-lookup"><span data-stu-id="2434a-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2434a-125">0</span><span class="sxs-lookup"><span data-stu-id="2434a-125">0</span></span> | <span data-ttu-id="2434a-126">関数呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="2434a-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2434a-127">コメント</span><span class="sxs-lookup"><span data-stu-id="2434a-127">Remarks</span></span>

<span data-ttu-id="2434a-128">この関数への呼び出しをラップする、 [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2434a-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](https://msdn.microsoft.com/library/aa391435(v=vs.85).aspx) method.</span></span>

<span data-ttu-id="2434a-129">このメソッドの呼び出しは、現在のオブジェクトがクラス定義である場合にのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2434a-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="2434a-130">メソッドの操作からは使用できない[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)インスタンスを指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="2434a-130">Method manipulation is not available from [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) pointers that point to instances.</span></span> <span data-ttu-id="2434a-131">メソッドが列挙される順序は、特定のインスタンスのバリアントすることは保証[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="2434a-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx).</span></span>

## <a name="requirements"></a><span data-ttu-id="2434a-132">要件</span><span class="sxs-lookup"><span data-stu-id="2434a-132">Requirements</span></span>  
 <span data-ttu-id="2434a-133">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2434a-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2434a-134">**ヘッダー:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2434a-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2434a-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2434a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2434a-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="2434a-136">See also</span></span>  
[<span data-ttu-id="2434a-137">WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2434a-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
