---
title: "文字列のマーシャリング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89dace5ba946f2c6bd1384f23ffcff797e99bdd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-strings"></a>文字列のマーシャリング
プラットフォーム呼び出しは、文字列のパラメーターをコピーし、必要な場合は、.NET Framework 形式 (Unicode) からアンマネージ形式 (ANSI) に変換します。 マネージ文字列は変更できないため、プラットフォーム呼び出しでは、関数から戻るときに、アンマネージ メモリからマネージ メモリに文字列がコピーされて戻されることはありません。  
  
 次の表では、文字列のマーシャリング オプションの一覧、それぞれの使用方法の説明、対応する .NET Framework サンプルへのリンクを示します。  
  
|String|説明|サンプル|  
|------------|-----------------|------------|  
|値渡し。|In パラメーターとして文字列を渡します。|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|結果として。|アンマネージ コードから文字列を返します。|[文字列](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|参照渡し。|<xref:System.Text.StringBuilder> を使って In/Out パラメーターとして文字列を渡します。|[バッファー](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|構造体で値渡し。|In パラメーターである構造体で文字列を渡します。|[構造体](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|構造体で参照渡し **(char\*)**。|In/Out パラメーターである構造体で文字列を渡します。 アンマネージ関数は文字バッファーへのポインターを必要とし、バッファー サイズは構造体のメンバーです。|[文字列](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|構造体で参照渡し **(char[])**。|In/Out パラメーターである構造体で文字列を渡します。 アンマネージ関数は、埋め込み文字バッファーを必要とします。|[OSInfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|クラスで値渡し **(char\*)**。|クラスで文字列を渡します (クラスは In/Out パラメーターです)。 アンマネージ関数は、文字バッファーへのポインターを必要とします。|[OpenFileDlg](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|クラスで値渡し **(char[])**。|クラスで文字列を渡します (クラスは In/Out パラメーターです)。 アンマネージ関数は、埋め込み文字バッファーを必要とします。|[OSInfo](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|文字列の配列として値渡し。|値によって渡される文字列の配列を作成します。|[配列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|文字列を含む構造体の配列として値渡し。|文字列を含む構造体の配列を作成し、配列を値で渡します。|[配列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>参照  
 [プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 [プラットフォーム呼び出しのデータ型](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [クラス、構造体、および共用体のマーシャリング](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)  
 [型の配列のマーシャリング](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)  
 [各種のマーシャリングのサンプル](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)
