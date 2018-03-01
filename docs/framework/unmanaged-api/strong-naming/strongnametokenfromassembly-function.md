---
title: "StrongNameTokenFromAssembly 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29414522eb2586b00ba3158d79155675cb468815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly 関数
指定したアセンブリ ファイルから、厳密な名前のトークンを作成します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]アセンブリのポータブル実行可能 (PE) ファイルへのパス。  
  
 `ppbStrongNameToken`  
 [out]厳密な名前が返されたトークンです。  
  
 `pcbStrongNameToken`  
 [out]厳密な名前のトークンのバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に終了します。それ以外の場合、`false`です。  
  
## <a name="remarks"></a>コメント  
 厳密な名前のトークンは、公開キーの短縮形です。 トークンは、アセンブリの署名に使用する公開キーから作成される 64 ビット ハッシュです。 トークンは、アセンブリの厳密な名前の一部であるし、アセンブリのメタデータから読み取ることができます。  
  
 トークンの作成後を呼び出す必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。  
  
 場合、`StrongNameTokenFromAssembly`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** mscoree.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [StrongNameTokenFromAssembly メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [StrongNameTokenFromAssemblyEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
