---
title: IsFrameworkAssembly 関数
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3fd130759ab11b54b597d5c099c33dab93070ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 関数
指定したアセンブリが管理されているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwzAssemblyReference`  
 [in]チェック対象のアセンブリの名前。  
  
 `pbIsFrameworkAssembly`  
 [out]アセンブリが管理されているかどうかを示すブール値。  
  
 `pwzFrameworkAssemblyIdentity`  
 [in]アセンブリの一意の id を表す uncanonicalized 文字列。  
  
 `pccSize`  
 [入力] `pwzFrameworkAssemblyIdentity` のサイズ。  
  
## <a name="remarks"></a>コメント  
 `pwzAssemblyReference`パラメーターは、アセンブリの名前を含む文字列へのポインター。  
  
 このアセンブリが .NET Framework の一部である場合、`pbIsFrameworkAssembly`パラメーターはブール値を含める`true`です。  
  
 名前付きのアセンブリが .NET Framework の一部ではない場合、または場合、`pwzAssemblyReference`パラメーターでは、アセンブリを指定しない場合`pbIsFrameworkAssembly`のブール値を含む`false`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Fusion グローバル静的関数](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
