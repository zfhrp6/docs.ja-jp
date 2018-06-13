---
title: ICorDebugFrame::GetCaller メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2452f4be0acde300676bf56011416e0a9ef16464
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411717"
---
# <a name="icordebugframegetcaller-method"></a>ICorDebugFrame::GetCaller メソッド
現在のこのフレームを呼び出したチェーン内 ICorDebugFrame オブジェクトへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppFrame`  
 [out]アドレスへのポインター、`ICorDebugFrame`を呼び出し元のフレームを表すオブジェクト。 この値は、呼び出されたフレームが現在のチェーン内の最も外側のフレームが場合は null です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
