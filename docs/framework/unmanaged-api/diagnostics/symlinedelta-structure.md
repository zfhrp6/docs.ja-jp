---
title: "SYMLINEDELTA 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: SYMLINEDELTA
api_location: diasymreader.dll
api_type: COM
f1_keywords: SYMLINEDELTA
helpviewer_keywords: SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbd83560516e946c03a0ea71cf79fe6d3396bacb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA 構造体
シンボル ハンドラーを編集した結果として移動されたメソッドに関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`mdMethod`|メソッドのメタデータ トークンです。|  
|`delta`|メソッドが移動された行の数。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl  
  
## <a name="see-also"></a>関連項目  
 [シンボル ストア診断構造体](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
