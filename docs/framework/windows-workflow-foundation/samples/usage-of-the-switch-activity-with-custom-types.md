---
title: "カスタム型を使用した Switch アクティビティの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# カスタム型を使用した Switch アクティビティの使用
このサンプルでは、<xref:System.Activities.> Statements.Switch`1?qualifyHint=False&autoUpgrade=True アクティビティを有効にしてユーザー定義の複合型を実行時に評価する方法について説明します。従来のほとんどの手続き型プログラミング言語では、[switch](http://go.microsoft.com/fwlink/?LinkId=180521) ステートメントで変数の条件の評価に基づいて実行ロジックを選択します。従来、`switch` ステートメントは、静的に評価できる式を対象としています。つまり、たとえば C\# では、プリミティブ型 \(<xref:System.Boolean>、<xref:System.Int32>、<xref:System.String>、列挙型など\) のみがサポートされます。  
  
 カスタム クラスで切り替えを有効にするには、カスタム複合型の値を実行時に評価するロジックを実装する必要があります。このサンプルでは、`Person` という名前のカスタム複合型で切り替えを有効にする方法を示します。  
  
-   カスタム クラス `Person` では、<xref:System.ComponentModel.TypeConverter> 属性がカスタム <xref:System.ComponentModel.TypeConverter> の名前で宣言されます。  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
  
    ```  
  
-   カスタム クラス `Person` では、<xref:System.Object.Equals%2A> クラスと <xref:System.Object.GetHashCode%2A> クラスがオーバーライドされます。  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
  
    ```  
  
-   カスタム クラスのインスタンスから文字列への変換、および文字列からカスタム クラスのインスタンスへの変換を行う、カスタム <xref:System.ComponentModel.TypeConverter> クラスが実装されます。  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 このサンプルには、次のファイルが含まれています。  
  
-   **Person.cs**: `Person` クラスを定義します。  
  
-   **PersonConverter.cs**: `Person` クラスの型コンバーター。  
  
-   **Sequence.xaml**: `Person` 型の切り替えを行うワークフロー。  
  
-   **Program.cs**: ワークフローを実行する main 関数。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] に Switch.sln を読み込みます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
3.  Ctrl キーを押しながら F5 キーを押してサンプルを実行します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## 参照  
 [ビルトイン アクティビティ ライブラリ](../../../../docs/framework/windows-workflow-foundation//net-framework-4-5-built-in-activity-library.md)