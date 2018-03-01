---
title: "StrongNameCompareAssemblies 関数"
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
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1ed98b1713427a71c73c30ddd64188f61d51045c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies 関数
2 つのアセンブリが厳密な名前の署名によってのみが異なるかどうかを判断します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wszAssembly1`  
 [in]最初のアセンブリへのパス。  
  
 `wszAssembly2`  
 [in]2 番目のアセンブリへのパス。  
  
 `pdwResult`  
 [out]次の値のいずれかです。  
  
-   `SN_CMP_DIFFERENT`(0) にアセンブリが別のデータを含むことを指定します。  
  
-   `SN_CMP_IDENTICAL`(1) - アセンブリが同じで、署名とチェックサムを含むでことを指定します。  
  
-   `SN_CMP_SIGONLY`(2) のアセンブリが署名およびチェックサムでのみが異なることを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に終了します。それ以外の場合、`false`です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>コメント  
 アセンブリの厳密な名前の署名は、アセンブリのテキストの名前、バージョン、カルチャ、および公開キー トークンで構成されます。  
  
 場合、`StrongNameCompareAssemblies`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="see-also"></a>参照  
 [StrongNameCompareAssemblies メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
