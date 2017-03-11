---
title: "方法: バイト配列を int に変換する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "バイト配列 [C#], 変換 (int に)"
  - "変換 [C#], バイト配列 (int に)"
ms.assetid: d6ac20e2-448e-4aea-99b9-faf04c6f1e79
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# 方法: バイト配列を int に変換する (C# プログラミング ガイド)
次の例では、<xref:System.BitConverter> クラスを使用してバイト配列を [int](../../../csharp/language-reference/keywords/int.md) に変換する方法、およびバイト配列に戻す方法を示しています。  ネットワークに接続せずにバイトを読み取った場合などは、その後バイトから組み込みデータ型への変換が必要になる場合もあります。  この例の [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> メソッド以外にも、バイト \(バイト配列\) を他の組み込み型に変換するメソッドがあります。<xref:System.BitConverter> クラス内のそのようなメソッドを次の表に示します。  
  
|戻される型|メソッド|  
|-----------|----------|  
|`bool`|[ToBoolean\(Byte\<xref:System.BitConverter.ToBoolean%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`char`|[ToChar\(Byte\<xref:System.BitConverter.ToChar%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`double`|[ToDouble\(Byte\<xref:System.BitConverter.ToDouble%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`short`|[ToInt16\(Byte\<xref:System.BitConverter.ToInt16%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`int`|[ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`long`|[ToInt64\(Byte\<xref:System.BitConverter.ToInt64%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`float`|[ToSingle\(Byte\<xref:System.BitConverter.ToSingle%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`ushort`|[ToUInt16\(Byte\<xref:System.BitConverter.ToUInt16%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`uint`|[ToUInt32\(Byte\<xref:System.BitConverter.ToUInt32%28System.Byte%5B%5D%2CSystem.Int32%29>|  
|`ulong`|[ToUInt64\(Byte\<xref:System.BitConverter.ToUInt64%28System.Byte%5B%5D%2CSystem.Int32%29>|  
  
## 使用例  
 この例ではバイト配列を初期化します。コンピューター アーキテクチャがリトル エンディアンの場合 \(つまり最下位バイトから先に格納される場合\)、配列を反転します。次に、[ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> メソッドを呼び出して、配列内の 4 バイトを `int` に変換します。  [ToInt32\(Byte\<xref:System.BitConverter.ToInt32%28System.Byte%5B%5D%2CSystem.Int32%29> の 2 番目の引数は、バイト配列の開始インデックスを指定します。  
  
> [!NOTE]
>  出力は、コンピューターのアーキテクチャのエンディアンによって異なる場合があります。  
  
 [!code-cs[csProgGuideTypes#22](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-byte-ar_1.cs)]  
  
## 使用例  
 この例では、<xref:System.BitConverter> クラスの <xref:System.BitConverter.GetBytes%28System.Int32%29> メソッドを呼び出して、`int` をバイトの配列に変換します。  
  
> [!NOTE]
>  出力は、コンピューターのアーキテクチャのエンディアンによって異なる場合があります。  
  
 [!code-cs[csProgGuideTypes#23](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-byte-ar_2.cs)]  
  
## 参照  
 <xref:System.BitConverter>   
 <xref:System.BitConverter.IsLittleEndian>   
 [型](../../../csharp/programming-guide/types/index.md)