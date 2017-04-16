---
title: "moduloObjectHashcode MDA | Microsoft Docs"
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
  - "managed debugging assistants (MDAs), hashcode modulus"
  - "Modulo object hash code"
  - "moduloObjectHashcode MDA"
  - "hashcode modulus"
  - "MDAs (managed debugging assistants), hashcode modulus"
  - "GetHashCode method"
  - "modulus of hashcodes"
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# moduloObjectHashcode MDA
`moduloObjectHashcode` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、<xref:System.Object> クラスの動作を変更し、<xref:System.Object.GetHashCode%2A> メソッドによって返されたハッシュ コードに対してモジュロ演算を実行します。  この MDA の既定の除数は 1 で、この場合、<xref:System.Object.GetHashCode%2A> はすべてのオブジェクトについて 0 \(ゼロ\) を返します。  
  
## 症状  
 共通言語ランタイム \(CLR: Common Language Runtime\) の新バージョンに移行した後、プログラムが正常に動作しなくなり、次のような症状を示します。  
  
-   プログラムが <xref:System.Collections.Hashtable> から不適切なオブジェクトを取得する。  
  
-   <xref:System.Collections.Hashtable> の列挙体の順序が変更され、プログラムが中断される。  
  
-   同等であった 2 つのオブジェクトが同等でなくなる。  
  
-   同等でなかった 2 つのオブジェクトが同等になる。  
  
## 原因  
 <xref:System.Collections.Hashtable> へのキーのクラスでの <xref:System.Object.Equals%2A> メソッドの実装が、<xref:System.Object.GetHashCode%2A> メソッドの呼び出し結果を比較して、オブジェクトが等しいかどうかをテストするため、プログラムが <xref:System.Collections.Hashtable> から不適切なオブジェクトを取得する可能性があります。  オブジェクトが等しいかどうかをテストする場合は、ハッシュ コードを使用しないでください。その理由は、2 つのオブジェクトが、それぞれのフィールドの値が異なる場合でも、同じハッシュ コードを使用している可能性があるからです。  このようなハッシュ コードの衝突は、実際にはまれですが発生することがあります。  この衝突が <xref:System.Collections.Hashtable> 検索に及ぼす影響で、同等でない 2 つのキーが同等であるかのように表示され、<xref:System.Collections.Hashtable> から不適切なオブジェクトが返されます。  パフォーマンス上の理由から、<xref:System.Object.GetHashCode%2A> の実装はランタイム バージョン間で変更される可能性があるため、あるバージョンで発生しない衝突が後続のバージョンで発生することがあります。  ハッシュ コードの衝突時にコードにバグがあるかどうかをテストするには、この MDA を有効にします。  この MDA を有効にすると、<xref:System.Object.GetHashCode%2A> メソッドが 0 \(ゼロ\) を返し、その結果、すべてのハッシュ コードが衝突します。  この MDA を有効にしたときのプログラムへの影響は、プログラムの実行速度が低下することだけです。  
  
 キーのハッシュ コードの計算に使用されるアルゴリズムが変更された場合は、<xref:System.Collections.Hashtable> からの列挙体の順序がランタイムのバージョン間で変化することがあります。  プログラムが、ハッシュ テーブルからのキーまたは値の列挙体の順序に依存しているかどうかをテストする場合は、この MDA を有効にできます。  
  
## 解決策  
 ハッシュ コードをオブジェクト ID の代用として使用しないでください。  ハッシュ コードを比較しない <xref:System.Object.Equals%2A?displayProperty=fullName> メソッドのオーバーライドを実装します。  
  
 ハッシュ テーブルのキーまたは値の列挙体の順序への依存関係を作成しないでください。  
  
## ランタイムへの影響  
 この MDA を有効にすると、アプリケーションの実行速度が低下します。  この MDA は、返されたハッシュ コードを受け取り、除数で除算したときの剰余を返すだけです。  
  
## 出力  
 この MDA には、出力がありません。  
  
## 構成  
 `modulus` 属性は、ハッシュ コードで使用する除数を指定します。  既定値は 1 です。  
  
```  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## 参照  
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)