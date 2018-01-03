---
title: "ICorDebugAppDomain2::GetArrayOrPointerType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetArrayOrPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6beb75638ccbf81149fd7fa1682acca3e7673dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType メソッド
指定された型、ポインター、または指定した型への参照の配列を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `elementType`  
 [in]CorElementType 列挙型 (配列、ポインター、または参照) を作成する基になるネイティブ型を指定の値です。  
  
 `nRank`  
 [in]配列のランク (つまり、ディメンションの数)。 場合、この値は 0 をする必要があります`elementType`ポインターまたは参照型を指定します。  
  
 `pTypeArg`  
 [in]配列の型を表す ICorDebugType オブジェクトへのポインター、ポインター、または参照を作成します。  
  
 `ppType`  
 [out]アドレスへのポインター、`ICorDebugType`構築された配列、ポインター型、または参照を表すオブジェクトを入力します。  
  
## <a name="remarks"></a>コメント  
 値*elementType*次のいずれかを指定する必要があります。  
  
-   ELEMENT_TYPE_PTR  
  
-   ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY またはインポートする場合  
  
 場合の値*elementType* ELEMENT_TYPE_PTR または ELEMENT_TYPE_BYREF、 *nRank* 0 にする必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
