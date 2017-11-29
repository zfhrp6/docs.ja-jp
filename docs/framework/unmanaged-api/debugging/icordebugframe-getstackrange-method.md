---
title: "ICorDebugFrame::GetStackRange メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame.GetStackRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f1db7617d52e07489ade339b76023e21816835ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange メソッド
このスタック フレームの絶対アドレス範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStart`  
 [out]ポインター、`CORDB_ADDRESS`これによって表されるスタック フレームの開始アドレスを指定する`ICorDebugFrame`オブジェクト。  
  
 `pEnd`  
 [out]ポインター、`CORDB_ADDRESS`これによって表されるスタック フレームの終了アドレスを指定する`ICorDebugFrame`オブジェクト。  
  
## <a name="remarks"></a>コメント  
 スタックのアドレス範囲は、複数のデバッグ エンジンから収集されインタリーブされたスタック トレースをつなぎ合わせてに役立ちます。 数値の範囲には、スタック フレームのコンテンツに関する情報は含まれません。 スタック フレームの場所の比較に対してのみ意味があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
