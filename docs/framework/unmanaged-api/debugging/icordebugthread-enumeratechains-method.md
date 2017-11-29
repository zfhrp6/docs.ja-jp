---
title: "ICorDebugThread::EnumerateChains メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.EnumerateChains
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b5a5da0a0053536ab4331e9d134464a4330500
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadenumeratechains-method"></a>ICorDebugThread::EnumerateChains メソッド
この ICorDebugThread オブジェクト内のすべてのスタック チェーンを含む ICorDebugChainEnum 列挙子へのインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppChains`  
 [out]アドレスへのポインター、`ICorDebugChainEnum`このスレッドは、アクティブな (つまり、最も最近) チェーンの先頭でチェーンでつながってオブジェクトにより、すべてのスタックの列挙体です。  
  
## <a name="remarks"></a>コメント  
 スタック チェーンでは、スレッドの物理呼び出し履歴を表します。 次の状況では、スタック チェーンの境界を作成します。  
  
-   アンマネージ コードへマネージまたはアンマネージからマネージへの遷移です。  
  
-   コンテキストの切り替え。  
  
-   A デバッガーのユーザー スレッドのハイジャックです。  
  
 純粋なマネージ コードを 1 つのコンテキストで実行されているスレッドの簡単な例で、一対一の対応は、スレッドとスタック チェーンの間存在します。  
  
 デバッガーは、論理呼び出し履歴にすべてのスレッドの物理呼び出し履歴を再配置する可能性があります。 これには、すべてのスレッドのチェーンの呼び出し元/呼び出し先の関係を順に並べ替えられ、それらが含まれます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
