---
title: "ICorDebugILFrame::GetIP メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79b18c6fe15e28b2cec07ef9dfaa06ee295ab42d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
