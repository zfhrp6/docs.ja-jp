---
title: "CreateCoreClrDebugTarget 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateCorClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5b05cc6c84f2f891691613a485d35d008ef79e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createcoreclrdebugtarget-function"></a>CreateCoreClrDebugTarget 関数
リモート コンピューターで実行しているデバッガー プロキシへの接続を作成、 [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)クエリ実行中のプロセスとリモート コンピューターに読み込まれたランタイムを使用できるオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwAddress`  
 [in] リモート対象コンピューターの IPv4 アドレス。  
  
 `ppTarget`  
 [out]ポインターへのポインター、 [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)作成されるオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。  
  
 E_OUTOFMEMORY  
 `ppTarget`  用に十分なメモリを割り当てることができません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 その他のエラーが発生しました。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CoreClrRemoteDebuggingInterfaces.h  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET framework のバージョン:** 3.5 SP1
