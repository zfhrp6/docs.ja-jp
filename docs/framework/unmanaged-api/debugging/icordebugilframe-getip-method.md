---
title: ICorDebugILFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd421d705a96778159cb80ad92d9ac654e88985f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414067"
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP メソッド
命令ポインターの値および命令ポインターの値の取得方法を説明するビットごとの組み合わせの値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pnOffset`  
 [out]命令ポインターの値。  
  
 `pMappingResult`  
 [out]命令ポインターの値が得られた方法を説明する CorDebugMappingResult 列挙値のビットごとの組み合わせへのポインター。  
  
## <a name="remarks"></a>コメント  
 命令ポインターの値は、関数の Microsoft intermediate language (MSIL) コードに、スタック フレームのオフセットです。 スタック フレームがアクティブな場合は、このアドレスは次の命令を実行するには。 スタック フレームがアクティブでない場合、このアドレスは、スタック フレームが再アクティブ化したときに実行する次の命令をします。  
  
 このフレームが・ イン タイム (JIT) コンパイルされたフレームの場合は、命令ポインターの値が値が概数のみであるために、実際のネイティブ命令ポインターから逆方向にマップすることによって決定されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
