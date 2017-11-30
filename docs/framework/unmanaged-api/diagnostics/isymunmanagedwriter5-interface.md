---
title: "ISymUnmanagedWriter5 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c5ac543ad98cc14382f0fb6d0d04fafa7136136e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 インターフェイス
ISymUnmanagedWriter5 インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスには、次のメソッドが含まれています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|マッピングの情報ソースへのトークンのスパンの特別なカスタム データ セクションを閉じます。 閉じた後は、以上のマッピング情報を追加できます。|  
|[MapTokenToSourceSpan メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|マップ指定されたソース行に指定したメタデータ トークンは、指定されたソース ファイルにわたっています。<br /><br /> 呼び出しの間で呼び出す必要があります[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)です。|  
|[OpenMapTokensToSourceSpans メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|マップする span トークンからソース情報を出力するカスタム データを特別なセクションを開きます。 メソッドは既に開かれて、またはその逆の場合、エラーは、このセクションの内容を開いています。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [シンボル ストア診断インターフェイスします。](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter4 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
