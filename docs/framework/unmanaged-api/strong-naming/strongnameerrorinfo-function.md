---
title: "StrongNameErrorInfo 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: StrongNameErrorInfo
helpviewer_keywords: StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e17ec04293f6274e307c66fc242c49bbdeee507
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo 関数
厳密な名前の関数のいずれかによって発生した最後のエラー コードを取得します。  
  
 この関数は廃止されました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>戻り値  
 厳密な名前の関数のいずれかによって設定、最終 COM エラー コード。  
  
## <a name="remarks"></a>コメント  
 厳密な名前のメソッドのほとんどは、単純なを返す`true`または`false`が正常に完了を示す値。 使用して、`StrongNameErrorInfo`を厳密な名前の関数によって生成された最後のエラーを示す HRESULT を取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [厳密な名前付けグローバル静的関数](http://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)
