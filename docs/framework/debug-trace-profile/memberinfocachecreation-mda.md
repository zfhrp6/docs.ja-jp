---
title: "memberInfoCacheCreation MDA | Microsoft Docs"
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
  - "member info cache creation"
  - "MemberInfoCacheCreation MDA"
  - "reflection, run-time errors"
  - "MDAs (managed debugging assistants), cache"
  - "cache [.NET Framework], reflection"
  - "managed debugging assistants (MDAs), cache"
  - "MemberInfo cache"
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# memberInfoCacheCreation MDA
`memberInfoCacheCreation` マネージ デバッグ アシスタント \(MDA: Managed Debugging Assistant\) は、<xref:System.Reflection.MemberInfo> キャッシュが作成されるとアクティブになります。  これにより、リソース ロードの大きいリフレクション機能を利用しているプログラムがあることがはっきりとわかります。  
  
## 症状  
 プログラムがリソース ロードの大きいリフレクションを使用しているため、プログラムの作業セットが増大します。  
  
## 原因  
 <xref:System.Reflection.MemberInfo> オブジェクトを使用するリフレクション操作はリソース ロードの大きい操作と見なされます。このような操作では、コールド ページに格納されているメタデータを読み取る必要があり、通常、プログラムである種の遅延バインディング シナリオを使用する必要があるためです。  
  
## 解決策  
 プログラムでリフレクションが使用されている場所を特定するには、この MDA を有効にしたうえで、コードをデバッガーで実行するか、または MDA がアクティブになったときにデバッガーに接続します。  デバッガーで、<xref:System.Reflection.MemberInfo> キャッシュの作成場所を示すスタック トレースを取得し、その場所から、プログラムがリフレクションを使用している場所を判別できます。  
  
 解決策は、コードの目的によって異なります。  この MDA により、プログラムが遅延バインディング シナリオを使用していることが警告されます。  事前バインディング シナリオに置き換えることができるかどうかを確認したり、遅延バインディング シナリオのパフォーマンスを検討したりする必要があります。  
  
## ランタイムへの影響  
 この MDA は、作成されるすべての <xref:System.Reflection.MemberInfo> キャッシュに対してアクティブになります。  パフォーマンスへの影響はほとんどありません。  
  
## 出力  
 MDA は、<xref:System.Reflection.MemberInfo> キャッシュが作成されたことを示すメッセージを出力します。  デバッガーを使用して、プログラムがリフレクションを使用している場所を示すスタック トレースを取得します。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 `memberInfoCacheCreation` MDA をアクティブにするサンプル コードを次に示します。  
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## 参照  
 <xref:System.Reflection.MemberInfo>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)