---
title: ICorDebugEval2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da4364e132e2a9d578a761eea77d0dfc8d0b92aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418237"
---
# <a name="icordebugeval2-interface1"></a><span data-ttu-id="b7952-102">ICorDebugEval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="b7952-102">ICorDebugEval2 Interface1</span></span>
<span data-ttu-id="b7952-103">"ICorDebugEval"の拡張のジェネリック型のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="b7952-103">Extends "ICorDebugEval" to provide support for generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7952-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-104">Methods</span></span>  
  
|<span data-ttu-id="b7952-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-105">Method</span></span>|<span data-ttu-id="b7952-106">説明</span><span class="sxs-lookup"><span data-stu-id="b7952-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7952-107">CallParameterizedFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-107">CallParameterizedFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|<span data-ttu-id="b7952-108">指定された"ICorDebugFunction"、型コンス トラクターが型パラメーターを受け取るか、型パラメーターを受け取り、それ自体の内部で入れ子にできるへの呼び出しを設定します。</span><span class="sxs-lookup"><span data-stu-id="b7952-108">Sets up a call to the specified "ICorDebugFunction", which can be nested inside a type whose constructor takes type parameters, or can itself take type parameters.</span></span>|  
|[<span data-ttu-id="b7952-109">CreateValueForType メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-109">CreateValueForType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|<span data-ttu-id="b7952-110">Null またはゼロの初期値を持つ新しい"ICorDebugValue"に指定した型のポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b7952-110">Gets a pointer to a new "ICorDebugValue" of the specified type, with an initial value of null or zero.</span></span>|  
|[<span data-ttu-id="b7952-111">NewParameterizedArray メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-111">NewParameterizedArray Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|<span data-ttu-id="b7952-112">指定した要素の型および次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b7952-112">Allocates a new array of the specified element type and dimensions.</span></span>|  
|[<span data-ttu-id="b7952-113">NewParameterizedObject メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-113">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|<span data-ttu-id="b7952-114">新しいパラメーター化された型のオブジェクトをインスタンス化し、オブジェクトのコンス トラクター メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b7952-114">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>|  
|[<span data-ttu-id="b7952-115">NewParameterizedObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|<span data-ttu-id="b7952-116">コンス トラクター メソッドを呼び出さずに、指定したクラスの新しい型のパラメーター化されたオブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="b7952-116">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method</span></span>|  
|[<span data-ttu-id="b7952-117">NewStringWithLength メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-117">NewStringWithLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|<span data-ttu-id="b7952-118">指定された内容を指定された長さの新しい文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="b7952-118">Creates a new string of the specified length with the specified contents.</span></span>|  
|[<span data-ttu-id="b7952-119">RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="b7952-119">RudeAbort Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|<span data-ttu-id="b7952-120">計算の中止この`ICorDebugEval2`は現在を実行します。</span><span class="sxs-lookup"><span data-stu-id="b7952-120">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7952-121">コメント</span><span class="sxs-lookup"><span data-stu-id="b7952-121">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7952-122">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="b7952-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7952-123">要件</span><span class="sxs-lookup"><span data-stu-id="b7952-123">Requirements</span></span>  
 <span data-ttu-id="b7952-124">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b7952-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7952-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7952-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7952-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7952-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7952-127">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7952-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7952-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7952-128">See Also</span></span>  
 [<span data-ttu-id="b7952-129">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7952-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
