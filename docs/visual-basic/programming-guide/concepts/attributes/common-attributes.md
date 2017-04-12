---
title: "一般的な属性 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f470e6ff3e316076d71a34346f741cc4504471a3
ms.lasthandoff: 03/13/2017

---
# <a name="common-attributes-visual-basic"></a>一般的な属性 (Visual Basic)
このトピックでは、Visual Basic プログラムで最もよく使用される属性について説明します。  
  
-   [グローバル属性](#Global)  
  
-   [旧式で属性](#Obsolete)  
  
-   [条件付きの属性](#Conditional)  
  
-   [呼び出し元情報属性](#CallerInfo)  
  
-   [Visual Basic の属性](#VB)  
  
##  <a name="Global"></a>グローバル属性  
 ほとんどの属性は、クラスやメソッドなどの特定の言語要素に適用されます。ただし、いくつかの属性がグローバルななど、アセンブリ全体またはモジュールに適用します。 たとえば、<xref:System.Reflection.AssemblyVersionAttribute>属性は、次のように、アセンブリにバージョン情報を埋め込むを使用することができます:</xref:System.Reflection.AssemblyVersionAttribute>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 グローバル属性は、いずれかの後、ソース コードに表示されます。 最上位`Imports`ステートメントと型、モジュール、または名前空間宣言の前にします。 グローバル属性が複数のソース ファイルで使用できますが、1 つのコンパイルのパスでファイルをコンパイルする必要があります。 Visual Basic プロジェクトで、一般に (Visual Studio でプロジェクトを作成するときに、ファイルが自動的に作成されます) AssemblyInfo.vb ファイル内にグローバル属性が配置されています。  
  
 アセンブリの属性は、アセンブリに関する情報を提供する値です。 これらは、次のカテゴリに分類されます。  
  
-   アセンブリの id 属性  
  
-   情報属性  
  
-   アセンブリ マニフェスト属性  
  
### <a name="assembly-identity-attributes"></a>アセンブリ ID 属性  
 (厳密な名前で、該当する場合) の&3; つの属性がアセンブリの id を決定します。 名前、バージョン、およびカルチャ。 これらの属性は、アセンブリの完全名を形成され、コードで参照するときに必要なれます。 アセンブリのバージョンと属性を使用してカルチャを設定することができます。 ただし、name の値をコンパイラは、Visual Studio IDE では設定、[アセンブリ情報 ダイアログ ボックス](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box)、またはアセンブリ リンカー (Al.exe) アセンブリが作成されると、アセンブリ マニフェストを含むファイルに基づいています。 <xref:System.Reflection.AssemblyFlagsAttribute>属性は、アセンブリの複数のコピーが共存できるかどうかを指定します</xref:System.Reflection.AssemblyFlagsAttribute>。  
  
 次の表は、id 属性を示します。  
  
|属性|目的|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>|アセンブリの id を完全に記述します。|  
|<xref:System.Reflection.AssemblyVersionAttribute></xref:System.Reflection.AssemblyVersionAttribute>|アセンブリのバージョンを指定します。|  
|<xref:System.Reflection.AssemblyCultureAttribute></xref:System.Reflection.AssemblyCultureAttribute>|アセンブリがサポートするカルチャを指定します。|  
|<xref:System.Reflection.AssemblyFlagsAttribute></xref:System.Reflection.AssemblyFlagsAttribute>|アセンブリが同じプロセスで、または同じアプリケーション ドメインでは、同じコンピューターにサイド バイ サイド実行をサポートするかどうかを指定します。|  
  
### <a name="informational-attributes"></a>情報属性  
 情報属性は、追加の会社情報または製品情報をアセンブリに指定する場合に使用できます。 次の表に、情報の属性で定義されている、<xref:System.Reflection?displayProperty=fullName>名前空間</xref:System.Reflection?displayProperty=fullName>。  
  
|属性|目的|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute></xref:System.Reflection.AssemblyProductAttribute>|アセンブリ マニフェストの製品名を指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyTrademarkAttribute></xref:System.Reflection.AssemblyTrademarkAttribute>|アセンブリ マニフェストの商標を指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute></xref:System.Reflection.AssemblyInformationalVersionAttribute>|アセンブリ マニフェストの補足バージョンを指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyCompanyAttribute></xref:System.Reflection.AssemblyCompanyAttribute>|アセンブリ マニフェストの会社名を指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyCopyrightAttribute></xref:System.Reflection.AssemblyCopyrightAttribute>|アセンブリ マニフェストの著作権情報を指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyFileVersionAttribute></xref:System.Reflection.AssemblyFileVersionAttribute>|Win32 ファイルのバージョンのリソースの特定のバージョン番号を使用するコンパイラに指示します。|  
|<xref:System.CLSCompliantAttribute></xref:System.CLSCompliantAttribute>|アセンブリが共通言語仕様 (CLS) に準拠しているかどうかを示します。|  
  
### <a name="assembly-manifest-attributes"></a>アセンブリ マニフェスト属性  
 アセンブリ マニフェスト属性を使用すると、アセンブリ マニフェストで情報を提供します。 これには、タイトル、説明、既定のエイリアス、および構成が含まれます。 次の表で定義されているアセンブリのマニフェスト属性、<xref:System.Reflection?displayProperty=fullName>名前空間</xref:System.Reflection?displayProperty=fullName>。  
  
|属性|目的|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute></xref:System.Reflection.AssemblyTitleAttribute>|アセンブリ マニフェストのアセンブリのタイトルを指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyDescriptionAttribute></xref:System.Reflection.AssemblyDescriptionAttribute>|アセンブリ マニフェストのアセンブリの説明を指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyConfigurationAttribute></xref:System.Reflection.AssemblyConfigurationAttribute>|アセンブリ マニフェストを (製品版またはデバッグ) などのアセンブリの構成を指定するカスタム属性を定義します。|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute></xref:System.Reflection.AssemblyDefaultAliasAttribute>|アセンブリ マニフェストのわかりやすい既定のエイリアスを定義します。|  
  
##  <a name="Obsolete"></a>旧式で属性  
 `Obsolete`属性は、いずれかの使用は推奨されなくプログラム エンティティをマークします。 不使用とマーク エンティティの使用、警告または属性の構成方法に応じて、エラーが生成されます。 例:  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 この例では、`Obsolete`クラスに属性が適用される`A`とメソッドに`B.OldMethod`します。 属性コンス トラクターの&2; 番目の引数が適用されるので`B.OldMethod`に設定されている`true`、クラスを使用する一方、このメソッドは、コンパイラ エラーになります`A`生成だけを警告されます。 呼び出す`B.NewMethod`で警告またはエラー。  
  
 属性コンス トラクターの&1; 番目の引数として指定された文字列が警告またはエラーの一部として表示されます。 たとえば、前の定義と共に使用する場合、次のコードには&2; つの警告と&1; つのエラーが生成されます。  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 クラスの&2; つの警告`A`生成: クラスの参照の宣言の&1; つ、クラス コンス トラクターのいずれかです。  
  
 `Obsolete`引数を指定せずに属性を使用できますが、理由の説明を含む、アイテムは今後使用しませんし、代わりに使用するをお勧めします。  
  
 `Obsolete`属性は、単一目的の属性であり、属性を使用するすべてのエンティティに適用できます。 `Obsolete`<xref:System.ObsoleteAttribute>。</xref:System.ObsoleteAttribute>エイリアスします。  
  
##  <a name="Conditional"></a>条件付きの属性  
 `Conditional`属性は、メソッドの実行をプリプロセッサ識別子に依存します。 `Conditional`属性は、エイリアスを<xref:System.Diagnostics.ConditionalAttribute>、メソッド、または属性クラスに適用できると</xref:System.Diagnostics.ConditionalAttribute>  
  
 この例では`Conditional`を有効にする、またはプログラム固有の診断情報の表示を無効にするメソッドに適用します。  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 場合、`TRACE_ON`識別子が定義されていませんが、トレース出力は表示されません。  
  
 `Conditional`属性は子と共によく使用、`DEBUG`次のようなトレースとデバッグ ビルドでは、内にないリリース ビルドのログ機能を有効にする識別子。  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 条件付きとしてマークされたメソッドが呼び出されると、指定のプリプロセッサ シンボルの有無は、呼び出しが含まれているか、省略したかどうかを決定します。 シンボルが定義されている、呼び出しが行われます。それ以外の場合、呼び出しは省略されます。 使用して`Conditional`は明快では、内のメソッドを囲む代わりに洗練され、エラーが減り`#if…#endif`ブロックは、次のようにします。  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 条件付きメソッドでは、クラスまたは構造体の宣言のメソッドである必要があり、戻り値を持つことはできません。  
  
### <a name="using-multiple-identifiers"></a>複数の識別子を使用します。  
 メソッドに複数`Conditional`属性、メソッドの呼び出しが含まれる少なくとも&1; つの条件付きのシンボルが定義されている場合 (つまり、シンボルが論理的に一緒にリンク OR 演算子を使用して)。 この例では、いずれかの存在に`A`または`B`メソッドの呼び出しになります。  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 AND 演算子を使用してシンボルを論理的にリンクの効果を実現するのには、シリアルの条件付きメソッドを定義できます。 場合にだけの次の&2; つ目のメソッドの実行など`A`と`B`が定義されています。  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a>属性クラスでの条件の使用  
 `Conditional`属性は、属性クラスの定義にも適用できます。 この例では、カスタム属性で`Documentation`デバッグが定義されている場合、メタデータに情報を追加のみができます。  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <a name="CallerInfo"></a>呼び出し元情報属性  
 呼び出し元情報の属性を使用すると、メソッドへの呼び出し元に関する情報を取得できます。 ソース コードのファイル パス、ソース コードと、呼び出し元のメンバー名の行番号を取得できます。  
  
 呼び出し元情報を取得するには、省略可能なパラメーターに適用される属性を使用します。 省略可能な各パラメーターでは、既定値を指定します。 次の表に、呼び出し元情報属性で定義されている、<xref:System.Runtime.CompilerServices?displayProperty=fullName>名前空間:</xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
|属性|説明|型|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|呼び出し元を含むソース ファイルのフル パスです。 これは、コンパイル時にパスです。|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|メソッドの呼び出し元のソース ファイルの行番号。|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|メソッド名または呼び出し元のプロパティ名。 詳細については、次を参照してください。[呼び出し元情報 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)します。|`String`|  
  
 呼び出し元情報属性の詳細については、次を参照してください。[呼び出し元情報 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md)します。  
  
##  <a name="VB"></a>Visual Basic の属性  
 次の表は、Visual Basic に固有の属性を示します。  
  
|属性|目的|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute>|クラスを COM オブジェクトとして公開する必要があることをコンパイラを示します。|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute>|モジュール メンバー モジュールに必要な修飾子のみを使用してアクセスを許可します。|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute>|固定長文字列のサイズを使用するための構造での入力し、出力ファイルを使用して指定の関数です。|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|固定長配列のサイズを使用するための構造での入力し、出力ファイルを使用して指定の関数です。|  
  
### <a name="comclassattribute"></a>大きく  
 使用`COMClassAttribute`を Visual Basic から COM コンポーネントを作成するプロセスを簡略化します。 COM オブジェクトは、.NET Framework アセンブリおよびせずにかなり異なる`COMClassAttribute`さまざまな Visual Basic から COM オブジェクトを生成する手順に従う必要があります。 マークされたクラスの`COMClassAttribute`コンパイラは、次の手順の多くを自動的に実行します。  
  
### <a name="hidemodulenameattribute"></a>HideModuleNameAttribute  
 使用`HideModuleNameAttribute`モジュール メンバー モジュールに必要な修飾子のみを使用してアクセスを許可するようにします。  
  
### <a name="vbfixedstringattribute"></a>VBFixedStringAttribute  
 使用`VBFixedStringAttribute`固定長文字列を作成する Visual Basic を強制的にします。 既定では、可変長の文字列し、この属性は、ファイルに文字列を格納するときに便利です。 次のコードでは、これを示しています。  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a>VBFixedArrayAttribute  
 使用`VBFixedArrayAttribute`サイズに固定されている配列を宣言します。 Visual Basic の文字列のような配列は、既定では可変長のこと。 この属性は、シリアル化またはファイルにデータを書き込む場合に便利です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Reflection></xref:System.Reflection>   
 <xref:System.Attribute></xref:System.Attribute>   
 [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)   
 [属性](https://msdn.microsoft.com/library/5x6cd29c)   
 [リフレクション (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)   
 [リフレクション (Visual Basic) を使用して属性へのアクセス](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
