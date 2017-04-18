---
title: "/link (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e98c855f0a0185e9d1b6682df9fc734e9f1f07bc
ms.lasthandoff: 03/13/2017

---
# <a name="link-visual-basic"></a>/link (Visual Basic)
コンパイラで指定したアセンブリ内の COM 型情報をコンパイル中のプロジェクトにできるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
/link:fileList  
' -or-  
/l:fileList  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileList`|必須です。 アセンブリ ファイル名のコンマ区切りリスト。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます。|  
  
## <a name="remarks"></a>コメント  
 `/link`  オプションでは、埋め込み型情報を含むアプリケーションを展開することができます。 アプリケーションは、ランタイム アセンブリへの参照を必要とせず、埋め込み型情報を実装するランタイム アセンブリで型を使用することができます。 ランタイム アセンブリのさまざまなバージョンがパブリッシュされると場合、埋め込み型情報を格納しているアプリケーションが再コンパイルすることがなく、さまざまなバージョンを操作できます。 例については、次を参照してください。[チュートリアル: マネージ アセンブリからの型の埋め込み](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)します。  
  
 使用して、`/link`オプションは、COM 相互運用機能を使用する場合に特に便利です。 アプリケーションが不要になったターゲット コンピューターのプライマリ相互運用機能アセンブリ (PIA) を必要とされるので、COM 型を埋め込むことができます。 `/link`オプションが生成されるコンパイル済みコードに参照された相互運用機能アセンブリから COM の型情報を埋め込むコンパイラに指示します。 COM の型は、CLSID (GUID) 値によって識別されます。 その結果、アプリケーションは、同じ CLSID 値を持つ同じ COM 型がインストールされているターゲット コンピューターで実行できます。 Microsoft Office を自動化するアプリケーションは、良い例です。 通常、Office のようなアプリケーションは、異なるバージョン間で同じの CLSID 値を維持、ので、アプリケーションは時間の長いとして .NET Framework 4 以降が対象のコンピューターにインストールされているし、アプリケーションのメソッド、プロパティ、または参照先の COM 型に含まれているイベントを使用して参照先の COM 型を使用できます。  
  
 `/link`オプションは、インターフェイス、構造、およびデリゲートを埋め込みます。 COM クラスの埋め込みはサポートされていません。  
  
> [!NOTE]
>  コードで埋め込みの COM 型のインスタンスを作成する場合は、適切なインターフェイスを使用してインスタンスを作成する必要があります。 コクラスを使用して埋め込み COM 型のインスタンスを作成しようと、エラーが発生します。  
  
 設定する、`/link`でオプション[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]、アセンブリ参照を追加し、設定、`Embed Interop Types`プロパティを**true**します。 既定値、`Embed Interop Types`プロパティは、 **false**します。  
  
 COM アセンブリ (アセンブリ A) にリンクする場合は、別の COM アセンブリ (アセンブリ B) を参照する、また、次のいずれかが true の場合は、アセンブリ B にリンクする必要があります。  
  
-   アセンブリ A から型の型から継承またはアセンブリ B のインターフェイスを実装します。  
  
-   フィールド、プロパティ、イベント、またはアセンブリ B の戻り値の型またはパラメーターの型を持つメソッドが呼び出されます。  
  
 使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を&1; つ以上のアセンブリ参照があるディレクトリを指定します。  
  
 ように、 [/reference](../../../visual-basic/reference/command-line-compiler/reference.md)コンパイラ オプション、`/link`コンパイラ オプションの参照が頻繁に使用すると、Vbc.rsp 応答ファイルを使用して[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリ。 使用して、 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)コンパイラ オプションと、Vbc.rsp ファイルを使用するコンパイラしたくない場合。  
  
 短い形式の`/link`は`/l`です。  
  
## <a name="generics-and-embedded-types"></a>ジェネリックおよび組み込み型  
 次のセクションでは、相互運用機能型の埋め込みのアプリケーションでジェネリック型の使用に関する制限事項について説明します。  
  
### <a name="generic-interfaces"></a>ジェネリック インターフェイス  
 相互運用機能アセンブリに埋め込まれているジェネリック インターフェイスは使用できません。 これを次の例に示します。  
  
 [!code-vb[VbLinkCompiler&#1;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a>ジェネリック パラメーターを持つ型  
 相互運用機能アセンブリから型を持つが埋め込まれているジェネリック パラメーターの種類は使用できない場合、外部のアセンブリから型であります。 この制限は、インターフェイスには適用されません。 たとえば、<xref:Microsoft.Office.Interop.Excel.Range>インターフェイスで定義されている、<xref:Microsoft.Office.Interop.Excel>アセンブリ</xref:Microsoft.Office.Interop.Excel></xref:Microsoft.Office.Interop.Excel.Range>。 ライブラリからの相互運用機能の型を埋め込んだ場合、<xref:Microsoft.Office.Interop.Excel>アセンブリと型を持つパラメーターを持つジェネリック型を返すメソッドは、公開、<xref:Microsoft.Office.Interop.Excel.Range>インターフェイスのメソッドは、次のコード例に示すように、ジェネリック インターフェイスを返す必要がある</xref:Microsoft.Office.Interop.Excel.Range></xref:Microsoft.Office.Interop.Excel>。  
  
 [!code-vb[VbLinkCompiler&#2;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler&#3;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler&4;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 次の例では、クライアント コードを返すメソッドを呼び出すことができます、<xref:System.Collections.IList>ジェネリック インターフェイスはエラーなし</xref:System.Collections.IList>。  
  
 [!code-vb[VbLinkCompiler&#5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a>例  
 次のコードは、ソース ファイルをコンパイル`OfficeApp.vb`からアセンブリを参照および`COMData1.dll`と`COMData2.dll`を生成する`OfficeApp.exe`です。  
  
```vb  
vbc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [チュートリアル: マネージ アセンブリから型の埋め込み](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [COM 相互運用の概要](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
