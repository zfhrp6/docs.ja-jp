---
title: "属性 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f9fc23cf7afbd28f0c9ae438cbce298cbf362fbd
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="attributes-c"></a>属性 (C#)
属性は、メタデータまたは宣言型の情報を、コード (アセンブリ、型、メソッド、プロパティなど) に関連付けるための優れた方法です。 属性をプログラム要素に関連付けると、*リフレクション*と呼ばれる手法を使用して、実行時にその属性を照会することができます。 詳細については、「[リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md)」を参照してください。  
  
 属性には、次の特徴があります。  
  
-   属性は、プログラムにメタデータを追加します。 *メタデータ*は、プログラムで定義された型に関する情報です。 すべての .NET アセンブリには、アセンブリで定義された型および型のメンバーを記述する、指定されたメタデータのセットが含まれます。 カスタム属性を追加して、必要な追加情報を指定することができます。 詳細については、「[カスタム属性の作成 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)」を参照してください。  
  
-   属性は、アセンブリ全体、モジュール、またはクラスやプロパティなどのより小さいプログラム要素に 1 つ以上適用することができます。  
  
-   属性は、メソッドやプロパティと同じ方法で引数を受け取ることができます。  
  
-   リフレクションを使用して、プログラム自身のメタデータや他のプログラムのメタデータを調べることができます。 詳しくは、「[リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)」をご覧ください。  
  
## <a name="using-attributes"></a>属性の使用  
 属性は、ほぼすべての宣言に配置できますが、属性によっては、有効な宣言の型が制限されている場合もあります。 C# では、角かっこ ([]) で囲んだ属性の名前を、適用先のエンティティの宣言の前に配置して、属性を指定します。  
  
 この例では、<xref:System.SerializableAttribute> 属性を使用してクラスに特性を適用します。  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 属性 <xref:System.Runtime.InteropServices.DllImportAttribute> を持つメソッドは次のように宣言されます。  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 宣言には、複数の属性を配置できます。  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 特定のエンティティで複数回指定できる属性もあります。 このような複数回指定できる属性の例として <xref:System.Diagnostics.ConditionalAttribute> があります。  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  慣例により、属性名はすべて "Attribute" という単語で終わります。これは、.NET Framework の他の項目と区別するためです。 ただし、コード内で属性を使用する場合は、attribute サフィックスを指定する必要はありません。 たとえば、`[DllImport]` は `[DllImportAttribute]` と同等ですが、.NET Framework では `DllImportAttribute` は属性の実際の名前を表します。  
  
### <a name="attribute-parameters"></a>属性のパラメーター  
 属性の多くは、位置指定パラメーター、名前のないパラメーター、または名前付きパラメーターを持っています。 位置指定パラメーターは、特定の順序で指定する必要があり、省略できません。名前付きパラメーターは省略可能で、任意の順序で指定することができます。 位置指定パラメーターは、最初に指定します。 たとえば、次の 3 つの属性は同等です。  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 最初のパラメーターである DLL 名は位置指定パラメーターであり、常に最初に指定されます。他のパラメーターは名前付きパラメーターです。 この例の場合、名前付きパラメーターの既定値はどちらも false なので、省略することができます。 パラメーターの既定値については、個々の属性のドキュメントを参照してください。  
  
### <a name="attribute-targets"></a>属性の対象  
 属性の*対象*は、属性が適用されるエンティティです。 たとえば、属性は、クラス、特定のメソッド、またはアセンブリ全体に適用できます。 既定では、属性は後に続く要素に適用されます。 ただし、明示的に指定すれば、メソッド、属性のパラメーター、属性の戻り値などにも適用できます。  
  
 属性の対象を明示的に識別するには、次の構文を使用します。  
  
```csharp  
[target : attribute-list]  
```  
  
 次の表に、使用可能な `target` の値を示します。  
  
|対象の値|対象|  
|------------------|----------------|  
|`assembly`|アセンブリ全体|  
|`module`|現在のアセンブリ モジュール|  
|`field`|クラスまたは構造体のフィールド|  
|`event`|イベント|  
|`method`|メソッドまたは `get` および `set` プロパティ アクセサー|  
|`param`|メソッド パラメーターまたは `set` プロパティ アクセサー パラメーター|  
|`property`|プロパティ|  
|`return`|メソッド、プロパティ インデクサー、または `get` プロパティ アクセサーの戻り値|  
|`type`|構造体、クラス、インターフェイス、列挙型、またはデリゲート|  
  
 次の例では、アセンブリとモジュールに属性を適用する方法を示します。 詳細については、「[共通の属性 (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)」を参照してください。  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 C# でメソッド、メソッドのパラメーター、およびメソッドの戻り値に属性を適用する方法の例を次に示します。  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  `SomeAttr` が有効になるように定義されるターゲットが何であっても、`return` は指定する必要があります。これは、`SomeAttr` が戻り値にのみ適用されるように定義されている場合でも必要です。 つまり、コンパイラは `AttributeUsage` 情報を使用して、あいまいな属性ターゲットを解決しません。 詳細については、「[AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)」を参照してください。  
  
## <a name="common-uses-for-attributes"></a>属性の一般的な使用法  
 次の表に、コードでの属性の一般的な使用法をいくつか示します。  
  
-   Web サービスの `WebMethod` 属性を使用してメソッドをマークして、メソッドが SOAP プロトコルを介して呼び出されるようにします。 詳細については、「<xref:System.Web.Services.WebMethodAttribute>」を参照してください。  
  
-   ネイティブ コードと相互運用するときにメソッドのパラメーターをマーシャリングする方法を記述します。 詳細については、「<xref:System.Runtime.InteropServices.MarshalAsAttribute>」を参照してください。  
  
-   クラス、メソッド、およびインターフェイスの COM プロパティを記述します。  
  
-   <xref:System.Runtime.InteropServices.DllImportAttribute> クラスを使用してアンマネージ コードを呼び出します。  
  
-   タイトル、バージョン、説明、または商標についてのアセンブリを記述します。  
  
-   永続化のためにシリアル化するクラスのメンバーを記述します。  
  
-   XML シリアル化のためにクラス メンバーと XML ノード間をマップする方法を記述します。  
  
-   メソッドのセキュリティ要件を記述します。  
  
-   セキュリティを適用するための特性を指定します。  
  
-   コードを容易にデバッグできる状態に保つために、ジャスト イン タイム (JIT) コンパイラによって最適化を制御します。  
  
-   メソッドの呼び出し元に関する情報を取得します。  
  
## <a name="related-sections"></a>関連項目  
 詳細については次を参照してください:  
  
-   [カスタム属性の作成 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [リフレクションを使用した属性へのアクセス (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [方法: 属性を使用して C/C++ の共用体を作成する (C#)](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [共通属性 (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [呼び出し元情報 (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../../csharp/programming-guide/index.md)  
 [リフレクション (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [属性](../../../../../docs/standard/attributes/index.md)
