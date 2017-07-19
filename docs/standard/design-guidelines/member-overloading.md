---
title: "メンバーのオーバー ロード | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "既定の引数"
  - "オーバー ロードされたメンバー [.NET Framework]"
  - "オーバー ロード メンバーのデザイン ガイドライン [.NET Framework]"
  - "オーバーロードされたメンバー"
  - "メンバーの署名"
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# メンバーのオーバー ロード
メンバーのオーバー ロードでは、数やパラメーターの種類においてのみ異なる場合、同じ名前が、同じ型に 2 つ以上のメンバーを作成することを意味します。 などの次に、 `WriteLine` メソッドはオーバー ロードします。  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
  
```  
  
 メソッド、コンス トラクター、およびインデックス付きプロパティは、パラメーターを持つことができます、ためメンバーのみがオーバー ロードできます。  
  
 オーバー ロードでは、使いやすさ、生産性、および再利用可能なライブラリの読みやすさを向上させるための最も重要な手法の 1 つです。 パラメーターの数のオーバー ロードにより、コンス トラクターおよびメソッドの単純なバージョンを提供できます。 パラメーターの型のオーバー ロードにより、さまざまな種類の選択されたセットに対して同じ操作を実行するメンバーに対して同じメンバー名を使用できます。  
  
 **✓ は** 短いオーバー ロードで使用される既定値を示すためにわかりやすいパラメーター名を使用しようとしています。  
  
 **X 回避** オーバー ロードのパラメーター名は任意で変更します。 1 つのオーバー ロードのパラメーターは、別のオーバー ロードのパラメーターと同じ入力を表している場合のパラメーターは、同じ名前である必要があります。  
  
 **X 回避** メンバーはオーバー ロードのパラメーターの順序で一貫性のあるできません。 同じ名前のパラメーターは、すべてのオーバー ロード内の同じ位置に表示されます。  
  
 **✓ は** 最長のオーバー ロードだけを仮想化 \(機能拡張が必要な場合\)。 短いオーバー ロードは必要がありますから長いオーバー ロードを呼び出すだけです。  
  
 **X のしないで** を使用して `ref` または `out` オーバー ロードされたメンバーに対する修飾子です。  
  
 一部の言語では、次のようにオーバー ロードの呼び出しを解決できません。 さらに、このようなオーバー ロード通常完全に異なるセマンティクスを持つし、おそらく必要がありますされませんオーバー ロードが 2 つの個別のメソッド代わりに。  
  
 **X のしないで** 同じ位置および類似した種類のパラメーターを使用して、まだ異なるセマンティクスを持つオーバー ロードがあります。  
  
 **✓ は**  許可 `null` 省略可能な引数に渡されます。  
  
 **✓ は** メンバーの既定の引数を持つメンバーを定義するのではなく、オーバー ロードを使用します。  
  
 既定の引数は、CLS 準拠ではありません。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [メンバー デザインのガイドライン](../../../docs/standard/design-guidelines/member.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)