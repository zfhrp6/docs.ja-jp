---
title: '方法 : リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: 1fa8029b8245aef5e10e9082a1038fd89fc1c84e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544732"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a>方法 : リフレクションを使用せずに印刷システム オブジェクトのプロパティを取得する
リフレクションを使用してオブジェクトのプロパティ (およびそれらのプロパティの型) と、アプリケーションのパフォーマンスが低下することができます。 <xref:System.Printing.IndexedProperties>名前空間は、リフレクションを使用してこの情報を取得するための手段を提供します。  
  
## <a name="example"></a>例  
 これを行うための手順は次のとおりです。  
  
1.  型のインスタンスを作成します。 次の例では、型は、<xref:System.Printing.PrintQueue>から派生した型の動作とほぼ同じコードでは、Microsoft .NET Framework に付属している型<xref:System.Printing.PrintSystemObject>です。  
  
2.  作成、<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>型から<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>です。 <xref:System.Collections.DictionaryEntry.Value%2A>このディクショナリ内の各エントリのプロパティから派生した型の 1 つのオブジェクトである<xref:System.Printing.IndexedProperties.PrintProperty>です。  
  
3.  ディクショナリのメンバーを列挙します。 各メンバーに、次のように操作します。  
  
4.  アップ キャストするには、各エントリの値<xref:System.Printing.IndexedProperties.PrintProperty>を使用して作成し、<xref:System.Printing.IndexedProperties.PrintProperty>オブジェクト。  
  
5.  型を取得、<xref:System.Printing.IndexedProperties.PrintProperty.Value%2A>のそれぞれの<xref:System.Printing.IndexedProperties.PrintProperty>オブジェクト。  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)
