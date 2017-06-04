---
title: "文字列のマーシャリング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "データ マーシャリング, プラットフォーム呼び出し"
  - "データ マーシャリング, サンプル"
  - "データ マーシャリング, 文字列"
  - "マーシャリング, プラットフォーム呼び出し"
  - "マーシャリング, サンプル"
  - "マーシャリング (文字列の)"
  - "プラットフォーム呼び出し, マーシャリング (データの)"
  - "サンプル アプリケーション [.NET Framework], マーシャリング (文字列の)"
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 文字列のマーシャリング
プラットフォーム呼び出しでは、文字列パラメーターがコピーされ、必要に応じて .NET Framework 形式 \(Unicode\) からアンマネージ形式 \(ANSI\) に変換されます。  マネージ文字列は変更不可なので、プラットフォーム呼び出しでは関数から制御が返されるときに、アンマネージ メモリからマネージ メモリへとマネージ文字列はコピーされません。  
  
 文字列に関するマーシャリングのオプションを次の表に列挙し、その使用方法を説明し、関連 .NET Framework サンプルへのリンクを示します。  
  
|\[文字列\]|Description|サンプル|  
|-------------|-----------------|----------|  
|値渡し。|文字列を In パラメーターとして渡します。|[MsgBox](../../../docs/framework/interop/msgbox-sample.md)|  
|結果として渡す。|アンマネージ コードから文字列を返します。|[Strings](http://msdn.microsoft.com/ja-jp/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|参照渡し。|<xref:System.Text.StringBuilder> を使用して、文字列を In\/Out パラメーターとして渡します。|[Buffers](http://msdn.microsoft.com/ja-jp/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|構造体に組み込んで値渡し。|文字列を In パラメーターである構造体に組み込んで渡します。|[構造体](http://msdn.microsoft.com/ja-jp/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|構造体に組み込んで参照渡し **\(char\*\)**。|文字列を In\/Out パラメーターである構造体に組み込んで渡します。  アンマネージ関数は文字バッファーへのポインターを要求します。またバッファーのサイズは構造体のメンバーです。|[Strings](http://msdn.microsoft.com/ja-jp/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|構造体に組み込んで参照渡し **\(char\[\]\)**。|文字列を In\/Out パラメーターである構造体に組み込んで渡します。  アンマネージ関数は埋め込み文字バッファーを要求します。|[OSInfo](http://msdn.microsoft.com/ja-jp/69d89067-507b-41fe-859d-30bf3ff29455)|  
|クラスに組み込んで値渡し **\(char\*\)**。|文字列をクラスに組み込んで渡します \(クラスは In\/Out パラメーターです\)。  アンマネージ関数は、文字バッファーへのポインターを要求します。|[OpenFileDlg](http://msdn.microsoft.com/ja-jp/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|クラスに組み込んで値渡し **\(char\[\]\)**。|文字列をクラスに組み込んで渡します \(クラスは In\/Out パラメーターです\)。  アンマネージ関数は埋め込み文字バッファーを要求します。|[OSInfo](http://msdn.microsoft.com/ja-jp/69d89067-507b-41fe-859d-30bf3ff29455)|  
|文字列の配列として値渡し。|値渡しされる文字列の配列を作成します。|[配列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|文字列を含む構造体の配列として値渡し。|文字列を含む構造体の配列を作成し、その配列を値渡しします。|[配列](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## 参照  
 [プラットフォーム呼び出しによるデータのマーシャリング](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/ja-jp/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [クラス、構造体、および共用体のマーシャリング](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md)   
 [Marshaling Arrays of Types](http://msdn.microsoft.com/ja-jp/049b1c1b-228f-4445-88ec-91bc7fd4b1e8)   
 [Miscellaneous Marshaling Samples](http://msdn.microsoft.com/ja-jp/a915c948-54e9-4d0f-a525-95a77fd8ed70)