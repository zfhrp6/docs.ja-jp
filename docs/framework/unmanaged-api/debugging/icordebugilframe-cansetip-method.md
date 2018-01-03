---
title: "ICorDebugILFrame::CanSetIP メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.CanSetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22d0df9add0a4ce35b1a590d65e30a6756fec49c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframecansetip-method"></a>ICorDebugILFrame::CanSetIP メソッド
Microsoft Intermediate Language (MSIL) コードで指定されたオフセット位置に、命令ポインターを設定しても安全かどうかを示す HRESULT を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `nOffset`  
 [in]命令ポインターの必要な設定です。  
  
## <a name="remarks"></a>コメント  
 使用して、`CanSetIP`メソッドを呼び出す前に、 [icordebugilframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)メソッドです。 場合`CanSetIP`HRESULT を返します、S_OK 以外を呼び出すことができますも`ICorDebugILFrame::SetIP`デバッガーがデバッグ中のコードの安全で適切な実行を続けることという保証はありません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug、h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
