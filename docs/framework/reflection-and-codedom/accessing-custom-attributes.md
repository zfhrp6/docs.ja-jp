---
title: "カスタム属性へのアクセス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "属性 [.NET Framework], アクセス"
  - "カスタム属性, アクセシビリティ"
  - "リフレクション, カスタム属性"
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# カスタム属性へのアクセス
プログラムの要素に属性を関連付けた後、リフレクションを使用して、属性の有無と属性値を照会できます。  .NET Framework Version 1.0 および 1.1 では、カスタム属性は実行コンテキストでチェックされます。  一方、.NET Framework Version 2.0 には、"リフレクションのみのコンテキスト" という新しい読み込みのコンテキストが用意されています。これを使用して、実行用に読み込むことができないコードをチェックできます。  
  
## リフレクションのみのコンテキスト  
 リフレクションのみのコンテキストに読み込まれたコードは実行できません。  つまり、カスタム属性のインスタンスを作成できません。カスタム属性のインスタンスを作成するには、そのコンストラクターを実行する必要があります。  リフレクションのみのコンテキストでカスタム属性を読み込んでチェックするには、<xref:System.Reflection.CustomAttributeData> クラスを使用します。  このクラスのインスタンスは、<xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=fullName> 静的メソッドの適切なオーバーロードを使用して取得できます。  「[方法 : リフレクションのみのコンテキストにアセンブリを読み込む](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)」を参照してください。  
  
## 実行コンテキスト  
 実行コンテキストの属性を照会するための主なリフレクション メソッドには、<xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=fullName> と <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName> があります。  
  
 カスタム属性のアクセシビリティの確認は、カスタム属性がアタッチされているアセンブリに対して行われます。  アクセシビリティを確認することは、カスタム属性がアタッチされているアセンブリ内の型に対するメソッドがカスタム属性のコンストラクターを呼び出すことができるかどうかを確認することと同じです。  
  
 <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=fullName> のようなメソッドは、型引数の参照可能範囲とアクセシビリティを確認します。  ユーザー定義型を含むアセンブリ内のコードだけが、**GetCustomAttributes** を使用してその型のカスタム属性を取得できます。  
  
 代表的なカスタム属性のデザイン パターンを次の C\# のコード例に示します。  この例は、ランタイム カスタム属性リフレクション モデルを示しています。  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 ランタイムが **GetLanguage** メソッドにアタッチされたパブリック カスタム属性型 <xref:System.ComponentModel.DescriptionAttribute> のカスタム属性の取得を試みる場合は、次のアクションを実行します。  
  
1.  ランタイムは、**Type.GetCustomAttributes** \(*type* 型\) への型引数 **DescriptionAttribute** がパブリックで、参照可能およびアクセス可能であることをチェックします。  
  
2.  **DescriptionAttribute** から派生したユーザー定義型 **MyDescriptionAttribute** が、**GetLanguage**\(\) メソッドに **DescriptionAttribute** がアタッチされている **System.Web.DLL** アセンブリ内で参照可能であり、アクセス可能であることを確認します。  
  
3.  **MyDescriptionAttribute** のコンストラクターが、**System.Web.DLL** アセンブリ内で参照可能であり、アクセス可能であることを確認します。  
  
4.  カスタム属性パラメーターを持つ **MyDescriptionAttribute** のコンストラクターを呼び出し、呼び出し元に新しいオブジェクトを返します。  
  
 カスタム属性リフレクション モデルが、ユーザー定義型のインスタンスを、その型が定義されているアセンブリの外部にリークする場合があります。  これは、[Type.GetMethods\(\)](frlrfSystemTypeClassGetMethodsTopic) のようなユーザー定義型のインスタンスを返すランタイム システム ライブラリ内のメンバーが、**RuntimeMethodInfo** オブジェクトの配列を返すのと同じです。  クライアントがユーザー定義のカスタム属性型についての情報を探索できないようにするには、その型のメンバーを非パブリックとして定義します。  
  
 リフレクションを使用してカスタム属性へのアクセス許可を取得する基本的な方法を次の例で示します。  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## 参照  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>   
 [型情報の表示](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [リフレクションに関するセキュリティ上の考慮事項](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)