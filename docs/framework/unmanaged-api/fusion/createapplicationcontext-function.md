---
title: "CreateApplicationContext 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateApplicationContext
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateApplicationContext
helpviewer_keywords: CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89c3181a157ce5162d93d1df14641b393fb3082d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createapplicationcontext-function"></a>CreateApplicationContext 関数
この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pName`  
 [in]フレンドリ名へのポインター。  
  
 `ppCtx`  
 [out]アプリケーション コンテキストへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** Fusion.dll 内のリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [IAssemblyCache インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
