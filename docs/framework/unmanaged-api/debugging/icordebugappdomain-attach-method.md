---
title: "ICorDebugAppDomain::Attach メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.Attach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::Attach
helpviewer_keywords:
- ICorDebugAppDomain::Attach method [.NET Framework debugging]
- Attach method [.NET Framework debugging]
ms.assetid: 0358b84a-4236-4c34-945b-4babff7df570
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25f6d32cc1b06615c592739ffab8a87f0fe5d5b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainattach-method"></a>ICorDebugAppDomain::Attach メソッド
アプリケーション ドメインに、デバッガーをアタッチします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Attach ();  
```  
  
## <a name="remarks"></a>コメント  
 アプリケーション ドメイン イベントを受信して、アプリケーション ドメインのデバッグを有効にするには、デバッガーをアタッチする必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
