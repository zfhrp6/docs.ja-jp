---
title: ICorDebugFunction::GetLocalVarSigToken メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a09741ed778436f1cb35d094885bd3effa813a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411595"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a>ICorDebugFunction::GetLocalVarSigToken メソッド
この ICorDebugFunction インスタンスで表される関数の場合は、ローカル変数シグネチャのメタデータ トークンを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pmdSig`  
 [out]ポインター、 `mdSignature` 、この関数の場合は、ローカル変数シグネチャのトークンまたは`mdSignatureNil`、この関数には、ローカル変数があるない場合。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
