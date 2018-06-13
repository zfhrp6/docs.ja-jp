---
title: ICorDebugFrame::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5da87071bc23ac17a3077049cd77f0fb8611439f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413021"
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
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
