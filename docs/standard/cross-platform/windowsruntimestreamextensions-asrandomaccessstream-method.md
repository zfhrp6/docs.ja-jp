---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream"
apilocation: 
  - "System.Runtime.WindowsRuntime.dll"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) メソッド
\[.NET Framework 4.5.1 以上でサポート\]  
  
 特定のストリームをランダム アクセス ストリームに変換します。  
  
 **名前空間**: <xref:System.IO?displayProperty=fullName>   
 **アセンブリ**: System.Runtime.WindowsRuntime \(System.Runtime.WindowsRuntime.dll 内\)  
  
## 構文  
  
```csharp  
[CLSCompliantAttribute(false)] public static  IRandomAccessStream AsRandomAccessStream(Stream stream)   
```  
  
```vb  
'Declaration <ExtensionAttribute> _ <CLSCompliantAttribute(False)> _ Public Shared Function AsRandomAccessStream ( _         stream As Stream) As IRandomAccessStream   
```  
  
#### パラメーター  
 `stream`  
  
 型: <xref:System.IO.Stream?displayProperty=fullName>   
 変換するストリーム。  
  
## 戻り値  
 型: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)   
 変換されたストリームを表す [!INCLUDE[wrt](../../../includes/wrt-md.md)] ランダム アクセス、ストリーム。  
  
## 例外  
  
|例外|状態|  
|--------|--------|  
|<xref:System.NotSupportedException>|変換するストリームがシークをサポートしていません。|  
  
## 解説  
 この拡張メソッドは、Windows ストア アプリを開発する場合のみに使用できます。  このメソッドは、Windows ストア アプリのストリームを使用する便利な方法を提供します。  変換する .NET Framework ストリームはシークをサポートする必要があります。  詳細については、<xref:System.IO.Stream.Seek%2A?displayProperty=fullName> メソッドを参照してください。  
  
> [!IMPORTANT]
>  この API は .NET Framework 4.5.1 以上ではサポートされますが、Version 4.5 ではサポートされません。  
  
## バージョン情報  
 **Windows ストア アプリ用 .NET**  
  
 Windows 8.1 でサポート  
  
## 参照  
 <xref:System.IO.WindowsRuntimeStreamExtensions>   
 [方法: .NET Framework ストリームと Windows ランタイム ストリームの間で変換を行う](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)