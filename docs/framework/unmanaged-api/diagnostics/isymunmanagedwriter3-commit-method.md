---
title: ISymUnmanagedWriter3::Commit メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e4e2cd49bdffd0a1293a5601cb44e4804e2b1ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428955"
---
# <a name="isymunmanagedwriter3commit-method"></a>ISymUnmanagedWriter3::Commit メソッド
ストリームにこれまでに書き込まれた変更をコミットします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Commit();  
```  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedWriter3 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
