---
title: "ジェネリックとリフレクション (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ジェネリック [C#], リフレクション"
  - "リフレクション [C#], ジェネリック型"
ms.assetid: 162fd9b4-dd5b-4abb-8c9b-e44e21e2f451
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# ジェネリックとリフレクション (C# プログラミング ガイド)
共通言語ランタイム \(CLR\) は、実行時にジェネリック型情報にアクセスできるため、非ジェネリック型の場合と同じように、リフレクションを使用してジェネリック型の情報を取得できます。  詳細については、「[ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)」を参照してください。  
  
 [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] では、ジェネリック型のランタイム情報を有効にするために <xref:System.Type> クラスに新しいメンバーが追加されています。  新しいメソッドとプロパティの使い方の詳細については、これらのクラスに関するドキュメントを参照してください。<xref:System.Reflection.Emit> 名前空間にも、ジェネリックをサポートする新しいメンバーが追加されています。  [方法: リフレクション出力を使用してジェネリック型を定義する](../Topic/How%20to:%20Define%20a%20Generic%20Type%20with%20Reflection%20Emit.md) を参照してください。  
  
 ジェネリック リフレクションで使用する用語に関する一定の条件の一覧については、<xref:System.Type.IsGenericType%2A> プロパティの解説を参照してください。  
  
|System.Type メンバー名|Description|  
|-----------------------|-----------------|  
|<xref:System.Type.IsGenericType%2A>|型がジェネリックの場合、true を返します。|  
|<xref:System.Type.GetGenericArguments%2A>|構築された型に対して指定された型引数、またはジェネリック型定義の型パラメーターを表す `Type` オブジェクトの配列を返します。|  
|<xref:System.Type.GetGenericTypeDefinition%2A>|現在の構築された型の基になっているジェネリック型定義を返します。|  
|<xref:System.Type.GetGenericParameterConstraints%2A>|現在のジェネリック型パラメーターの制約を表す `Type` オブジェクトの配列を返します。|  
|<xref:System.Type.ContainsGenericParameters%2A>|型、またはその型を囲む型またはメソッドのいずれかに、特定の型が指定されていない型パラメーターが含まれている場合、true を返します。|  
|<xref:System.Type.GenericParameterAttributes%2A>|現在のジェネリック型パラメーターの特別な制約を表す `GenericParameterAttributes` フラグの組み合わせを取得します。|  
|<xref:System.Type.GenericParameterPosition%2A>|型パラメーターを表す `Type` オブジェクトの場合、型パラメーターを宣言したジェネリック型定義またはジェネリック メソッド定義の型パラメーター リストで型パラメーターの位置を取得します。|  
|<xref:System.Type.IsGenericParameter%2A>|現在の `Type` が、ジェネリック型定義またはジェネリック メソッド定義の型パラメーターを表しているかどうかを示す値を取得します。|  
|<xref:System.Type.IsGenericTypeDefinition%2A>|現在の <xref:System.Type> が、他のジェネリック型を構築できるジェネリック型定義を表しているかどうかを示す値を取得します。  型がジェネリック型定義を表している場合、true を返します。|  
|<xref:System.Type.DeclaringMethod%2A>|現在のジェネリック型パラメーターを定義したジェネリック メソッドを返します。型パラメーターがジェネリック メソッドによって定義されていない場合は null を返します。|  
|<xref:System.Type.MakeGenericType%2A>|現在のジェネリック型定義の型パラメーターを型の配列要素に置き換え、その結果構築された型を表す <xref:System.Type> オブジェクトを返します。|  
  
 さらに、ジェネリック メソッドのランタイム情報を有効にする新しいメンバーが <xref:System.Reflection.MethodInfo> クラスに追加されています。  ジェネリック メソッドのリフレクションで使用する用語に関する一定の条件の一覧については、<xref:System.Reflection.MethodInfo.IsGenericMethod%2A> プロパティの解説を参照してください。  
  
|System.Reflection.MemberInfo メンバー名|Description|  
|----------------------------------------|-----------------|  
|<xref:System.Reflection.MethodInfo.IsGenericMethod%2A>|メソッドがジェネリックの場合、true を返します。|  
|<xref:System.Reflection.MethodInfo.GetGenericArguments%2A>|構築されたジェネリック メソッドの型引数、またはジェネリック メソッド定義の型パラメーターを表す Type オブジェクトの配列を返します。|  
|<xref:System.Reflection.MethodInfo.GetGenericMethodDefinition%2A>|現在の構築されたメソッドの基になっているジェネリック メソッド定義を返します。|  
|<xref:System.Reflection.MethodInfo.ContainsGenericParameters%2A>|メソッド、またはそれを囲む型のいずれかに、特定の型が指定されていない型パラメーターが含まれている場合、true を返します。|  
|<xref:System.Reflection.MethodInfo.IsGenericMethodDefinition%2A>|現在の <xref:System.Reflection.MethodInfo> がジェネリック メソッド定義を表している場合、true を返します。|  
|<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>|現在のジェネリック メソッド定義の型パラメーターを型の配列要素に置き換え、その結果構築されるメソッドを表す <xref:System.Reflection.MethodInfo> オブジェクトを返します。|  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../csharp/programming-guide/generics/index.md)   
 [リフレクションとジェネリック型](../Topic/Reflection%20and%20Generic%20Types.md)   
 [ジェネリック](../Topic/Generics%20in%20the%20.NET%20Framework.md)