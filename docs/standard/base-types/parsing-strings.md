---
title: ".NET Framework における文字列の解析 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "解析 (文字列を)、文字列の解析の概要"
  - "IFormatProvider インターフェイス、解析 (文字列を)"
  - "基本型、解析 (文字列を)"
  - "Parse メソッド"
  - "解析 (文字列を)"
ms.assetid: 5e758b41-db93-456b-8999-99b7304b090d
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# .NET Framework における文字列の解析
解析操作では、.NET Framework の基本型を表す文字列を .NET Framework 基本型に変換します。  たとえば、解析操作は、文字列を浮動小数点値または日付と時刻の値に変換するために使用されます。  解析操作に使用される最も一般的なメソッドは `Parse` メソッドです。  解析は、基本型をその文字列形式に変換する書式指定の逆の操作であるため、書式指定時の規則の多くが解析にも適用されます。  書式指定で <xref:System.IFormatProvider> インターフェイスを実装するオブジェクトを使用してカルチャに依存した書式指定情報を提供するのと同じように、解析でも <xref:System.IFormatProvider> インターフェイスを実装するオブジェクトを使用して、文字列形式の解釈方法が決定されます。  詳細については、「[型の書式設定](../../../docs/standard/base-types/formatting-types.md)」を参照してください。  
  
## このセクションの内容  
 [数値文字列の解析](../../../docs/standard/base-types/parsing-numeric.md)  
 文字列を .NET Framework の数値型に変換する方法について説明します。  
  
 [日付と時刻文字列の解析](../../../docs/standard/base-types/parsing-datetime.md)  
 文字列を .NET Framework の **DateTime** 型に変換する方法について説明します。  
  
 [その他の文字列の解析](../../../docs/standard/base-types/parsing-other.md)  
 文字列を **Char** 型、**Boolean** 型、および **Enum** 型に変換する方法について説明します。  
  
## 関連項目  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)  
 書式指定子や書式プロバイダーなど、基本的な書式指定の概念について説明します。  
  
 [.NET Framework における型変換](../../../docs/standard/base-types/type-conversion.md)  
 型の変換方法について説明します。  
  
 [基本型](../../../docs/standard/base-types/index.md)  
 .NET Framework の基本型に対して実行できる一般的な操作について説明します。