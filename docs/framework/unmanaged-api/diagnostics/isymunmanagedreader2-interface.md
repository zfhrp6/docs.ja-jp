---
title: "ISymUnmanagedReader2 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2
helpviewer_keywords: ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b23e166249659b94d454070c01c003495d1018a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2 インターフェイス
ドキュメント、メソッド、およびシンボル ストア内の変数へのアクセスを提供するシンボル リーダーを表します。 このインターフェイスは、 [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)インターフェイスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|指定したメソッドのトークンと、エディット コンティニュ バージョン番号、シンボル リーダー メソッドを取得します。|  
|[GetMethodsInDocument メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|指定のドキュメントに行情報を持つすべてのメソッドを取得します。|  
|[GetSymAttributePreRemap メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|その名前に基づくカスタム属性を取得します。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [シンボル ストア診断インターフェイスします。](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedReader インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
