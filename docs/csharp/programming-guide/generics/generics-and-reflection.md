---
title: "ジェネリックとリフレクション (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], reflection
- reflection [C#], generic types
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cea1f48f336e4c73fa317d1cbbab3d06ceb6045f
ms.lasthandoff: 03/13/2017

---
# <a name="generics-and-reflection-c-programming-guide"></a>ジェネリックとリフレクション (C# プログラミング ガイド)
共通言語ランタイム (CLR) は実行時にジェネリック型の情報にアクセスできるため、非ジェネリック型の場合と同じように、リフレクションを使用してジェネリック型の情報を取得できます。 詳細については、「[ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)」を参照してください。  
  
 [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] には、ジェネリック型の実行時の情報を有効にする新しいメンバーがいくつか <xref:System.Type> クラスに追加されています。 それらのメソッドとプロパティの使用方法の詳細については、そのクラスのドキュメントを参照してください。 <xref:System.Reflection.Emit> 名前空間にも、ジェネリックをサポートする新しいメンバーが追加されています。 「[方法: リフレクション出力を使用してジェネリック型を定義する](http://msdn.microsoft.com/library/07d5f01a-7b5b-40ea-9b15-f21561098fe4)」を参照してください。  
  
 ジェネリック リフレクションで使用される用語に関する一定条件の一覧については、<xref:System.Type.IsGenericType%2A> プロパティの解説を参照してください。  
  
|System.Type メンバー名|説明|  
|-----------------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|型がジェネリックである場合に true を返します。|  
|<xref:System.Type.GetGenericArguments%2A>|構築された型に対して指定された型引数、またはジェネリック型定義の型パラメーターを表す `Type` オブジェクトの配列を返します。|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|現在構築されている型の基になるジェネリック型定義を返します。|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|現在のジェネリック型パラメーターの制約を表す `Type` オブジェクトの配列を返します。|  
|<xref:System.Type.ContainsGenericParameters%2A>|型 (またはそこに含まれているいずれかの型またはメソッド) に、具体的な型の指定されていない型パラメーターが含まれている場合に true を返します。|  
|<xref:System.Type.GenericParameterAttributes%2A>|現在のジェネリック型パラメーターの特殊な制約を説明する `GenericParameterAttributes` フラグの組み合わせを取得します。|  
|<xref:System.Type.GenericParameterPosition%2A>|型パラメーターを表す `Type` オブジェクトの場合、その型パラメーターが宣言されたジェネリック型定義またはジェネリック メソッド定義の型パラメーター リストにおけるその位置を取得します。|  
|<xref:System.Type.IsGenericParameter%2A>|現在の `Type` が、ジェネリック型定義またはジェネリック メソッド定義の型パラメーターを表すかどうかを示す値を取得します。|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|現在の <xref:System.Type> が、他のジェネリック型を構築できるジェネリック型の定義を表しているかどうかを示す値を取得します。 その型がジェネリック型の定義を表している場合に true を返します。|  
|<xref:System.Type.DeclaringMethod%2A>|現在のジェネリック型パラメーターを定義したジェネリック メソッドを返します。その型パラメーターがジェネリック メソッドによって定義されたものではない場合は null を返します。|  
|<xref:System.Type.MakeGenericType%2A>|型の配列の要素を現在のジェネリック型定義の型パラメーターで置き換え、結果の構築型を表す <xref:System.Type> オブジェクトを返します。|  
  
 さらに、ジェネリック メソッドの実行時の情報を有効にする新しいメンバーが <xref:System.Reflection.MethodInfo> クラスに追加されています。 ジェネリック メソッドのリフレクションで使用される用語の一定条件の一覧については、<xref:System.Reflection.MethodInfo.IsGenericMethod%2A> プロパティの解説を参照してください。  
  
|System.Reflection.MemberInfo メンバー名|説明|  
|----------------------------------------------|-----------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|メソッドがジェネリックである場合に true を返します。|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|構築されたジェネリック メソッドの型引数、またはジェネリック メソッド定義の型パラメーターを表す Type オブジェクトの配列を返します。|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|現在構築されているメソッドの基になるジェネリック メソッド定義を返します。|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|メソッド (またはそこに含まれているいずれかの型) に、具体的な型の指定されていない型パラメーターが含まれている場合に true を返します。|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|現在の <xref:System.Reflection.MethodInfo> がジェネリック メソッドの定義を表している場合に true を返します。|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|現在のジェネリック メソッド定義の型パラメーターを型の配列要素に置き換え、その結果構築されるメソッドを表す <xref:System.Reflection.MethodInfo> オブジェクトを返します。|  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../csharp/programming-guide/generics/index.md)   
 [リフレクションとジェネリック型](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)   
 [ジェネリック](https://msdn.microsoft.com/library/ms172192)
