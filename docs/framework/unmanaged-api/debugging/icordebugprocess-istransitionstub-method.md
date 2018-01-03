---
title: "ICorDebugProcess::IsTransitionStub メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.IsTransitionStub
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fe38cf5f53c2514b845238c1d52fa12df526fdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub メソッド
マネージ コードへの遷移を発生させるスタブ内にアドレスがあるかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [in]A`CORDB_ADDRESS`対象のアドレスを指定する値。  
  
 `pbTransitionStub`  
 [out]ブール値へのポインター`true`場合は、指定したアドレスがマネージ コードへの遷移を発生させるスタブ内のそれ以外の場合 *`pbTransitionStub`は`false`します。  
  
## <a name="remarks"></a>コメント  
 `IsTransitionStub`をマネージ ステッパをステップ実行の制御を返すタイミングを決定するアンマネージのステップ実行のコードでメソッドを使用できます。  
  
 こともできます identity 遷移スタブ ポータブル実行可能 (PE) ファイルに情報を参照しています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
