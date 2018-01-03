---
title: "IBindingDisplay::InitializeForProcess メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.InitializeForProcess
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56f55788fcaf08507f413a03c5364ce3bcdbbf3c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ibindingdisplayinitializeforprocess-method"></a>IBindingDisplay::InitializeForProcess メソッド
初期化、 [IBindingDisplay](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pid`  
 [in]プロセス識別子。  
  
## <a name="remarks"></a>コメント  
 デバッガーの呼び出し、`InitializeForProcess`メソッド作成時にバインディングの表示を初期化します。 `InitializeForProcess`その他のメソッドの前に、作成時に呼び出す必要があります`IBindingDisplay`と呼びます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** BindingDisplay.h  
  
 **ライブラリ:** BindingDisplay.idl  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IBindingDisplay インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
