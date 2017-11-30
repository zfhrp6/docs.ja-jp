---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79e93a44f2cc532286a7e9b01fa32292a4e1c69a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="86a68-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="86a68-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="86a68-103">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="86a68-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="86a68-104">型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="86a68-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86a68-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="86a68-105">Methods</span></span>  
  
|<span data-ttu-id="86a68-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="86a68-106">Method</span></span>|<span data-ttu-id="86a68-107">説明</span><span class="sxs-lookup"><span data-stu-id="86a68-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86a68-108">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="86a68-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="86a68-109">このクラスを定義するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="86a68-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="86a68-110">GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="86a68-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="86a68-111">指定された静的フィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="86a68-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="86a68-112">GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="86a68-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="86a68-113">取得、`TypeDef`このクラスのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="86a68-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86a68-114">コメント</span><span class="sxs-lookup"><span data-stu-id="86a68-114">Remarks</span></span>  
 <span data-ttu-id="86a68-115">`ICorDebugClass`インターフェイスはインスタンス化されていないジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="86a68-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="86a68-116">ICorDebugType インターフェイスでは、ジェネリック型のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="86a68-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="86a68-117">たとえば、`Hashtable<K, V>`で表されます`ICorDebugClass`であるのに対し`Hashtable<Int32, String>`で表されます`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="86a68-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="86a68-118">非ジェネリック型は型が両方によって表される`ICorDebugClass`と`ICorDebugType`です。</span><span class="sxs-lookup"><span data-stu-id="86a68-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="86a68-119">後者のインターフェイスは、型のインスタンス化に対処するには、.NET Framework version 2.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="86a68-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86a68-120">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="86a68-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86a68-121">要件</span><span class="sxs-lookup"><span data-stu-id="86a68-121">Requirements</span></span>  
 <span data-ttu-id="86a68-122">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="86a68-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86a68-123">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86a68-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86a68-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86a68-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86a68-125">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86a68-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86a68-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="86a68-126">See Also</span></span>  
 [<span data-ttu-id="86a68-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="86a68-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
