---
title: "ICorDebugEval2::NewParameterizedObject メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29b2470f50e96307ad91428fe1c712e7340baa32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="6b9ae-102">ICorDebugEval2::NewParameterizedObject メソッド</span><span class="sxs-lookup"><span data-stu-id="6b9ae-102">ICorDebugEval2::NewParameterizedObject Method</span></span>
<span data-ttu-id="6b9ae-103">新しいパラメーター化された型のオブジェクトをインスタンス化し、オブジェクトのコンス トラクター メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9ae-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b9ae-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b9ae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b9ae-105">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="6b9ae-106">[in]ICorDebugFunction を表すオブジェクトをインスタンス化するオブジェクトのコンス トラクターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="6b9ae-107">[in]型引数の数が渡されます。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="6b9ae-108">[in]ICorDebugType を表すオブジェクトがインスタンス化されるオブジェクトの型引数が指すそれぞれが、ポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="6b9ae-109">[in]引数の数は、コンス トラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="6b9ae-110">[in]それぞれのオブジェクトをポイントする ICorDebugValue コンス トラクターに渡される引数の値を表す、ポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b9ae-111">コメント</span><span class="sxs-lookup"><span data-stu-id="6b9ae-111">Remarks</span></span>  
 <span data-ttu-id="6b9ae-112">オブジェクトのコンス トラクターがかかる場合があります<xref:System.Type>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b9ae-113">要件</span><span class="sxs-lookup"><span data-stu-id="6b9ae-113">Requirements</span></span>  
 <span data-ttu-id="6b9ae-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b9ae-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b9ae-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b9ae-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b9ae-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b9ae-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b9ae-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b9ae-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
