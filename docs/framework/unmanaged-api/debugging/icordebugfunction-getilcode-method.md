---
title: "ICorDebugFunction::GetILCode メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction.GetILCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da955f6eb8e7480fb23192e1a77341166dd40f3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctiongetilcode-method"></a>ICorDebugFunction::GetILCode メソッド
この ICorDebugFunction オブジェクトに関連付けられている Microsoft intermediate language (MSIL) コードを表す ICorDebugCode インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppCode`  
 [out]ポインター、`ICorDebugCode`インスタンス、または関数が MSIL にコンパイルされていない場合は null です。  
  
## <a name="remarks"></a>コメント  
 この関数でエディット コンティニュが許可されている場合、`GetILCode`メソッドは、共通言語ランタイム (CLR) 内のコードのこの関数の編集済みのバージョンに対応する MSIL コードを取得します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
