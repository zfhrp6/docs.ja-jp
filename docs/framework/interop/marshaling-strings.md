---
title: 文字列のマーシャリング
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52a78e0c3969e879bf2fd1b1f5c41b2caac2ba11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391122"
---
# <a name="marshaling-strings"></a>文字列のマーシャリング
プラットフォーム呼び出しは、文字列のパラメーターをコピーし、必要な場合は、.NET Framework 形式 (Unicode) からアンマネージ形式 (ANSI) に変換します。 マネージ文字列は変更できないため、プラットフォーム呼び出しでは、関数から戻るときに、アンマネージ メモリからマネージ メモリに文字列がコピーされて戻されることはありません。  
  
 次の表では、文字列のマーシャリング オプションの一覧、それぞれの使用方法の説明、対応する .NET Framework サンプルへのリンクを示します。  
  
|String|説明|サンプル|  
|------------|-----------------|------------|  
|値渡し。|In パラメーターとして文字列を渡します。|[MsgBox](msgbox-sample.md)|  
|結果として。|アンマネージ コードから文字列を返します。|[文字列](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|参照渡し。|<xref:System.Text.StringBuilder> を使って In/Out パラメーターとして文字列を渡します。|[バッファー](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100))|  
|構造体で値渡し。|In パラメーターである構造体で文字列を渡します。|[構造体](https://msdn.microsoft.com/library/96a62265-dcf9-4608-bc0a-1f762ab9f48e(v=vs.100))|  
|構造体で参照渡し **(char\*)**。|In/Out パラメーターである構造体で文字列を渡します。 アンマネージ関数は文字バッファーへのポインターを必要とし、バッファー サイズは構造体のメンバーです。|[文字列](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))|  
|構造体で参照渡し **(char[])**。|In/Out パラメーターである構造体で文字列を渡します。 アンマネージ関数は、埋め込み文字バッファーを必要とします。|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|クラスで値渡し **(char\*)**。|クラスで文字列を渡します (クラスは In/Out パラメーターです)。 アンマネージ関数は、文字バッファーへのポインターを必要とします。|[OpenFileDlg](https://msdn.microsoft.com/library/b7dea792-cb92-4baf-ac7b-6a24803e6c75(v=vs.100))|  
|クラスで値渡し **(char[])**。|クラスで文字列を渡します (クラスは In/Out パラメーターです)。 アンマネージ関数は、埋め込み文字バッファーを必要とします。|[OSInfo](https://msdn.microsoft.com/library/69d89067-507b-41fe-859d-30bf3ff29455(v=vs.100))|  
|文字列の配列として値渡し。|値によって渡される文字列の配列を作成します。|[配列](marshaling-different-types-of-arrays.md)|  
|文字列を含む構造体の配列として値渡し。|文字列を含む構造体の配列を作成し、配列を値で渡します。|[配列](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>参照  
 [プラットフォーム呼び出しによるデータのマーシャリング](marshaling-data-with-platform-invoke.md)  
 [プラットフォーム呼び出しのデータ型](https://msdn.microsoft.com/library/16014d9f-d6bd-481e-83f0-df11377c550f(v=vs.100))  
 [クラス、構造体、および共用体のマーシャリング](marshaling-classes-structures-and-unions.md)  
 [型の配列のマーシャリング](https://msdn.microsoft.com/library/049b1c1b-228f-4445-88ec-91bc7fd4b1e8(v=vs.100))  
 [各種のマーシャリングのサンプル](https://msdn.microsoft.com/library/a915c948-54e9-4d0f-a525-95a77fd8ed70(v=vs.100))
