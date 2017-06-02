---
title: "方法 : JSON データをシリアル化および逆シリアル化する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# 方法 : JSON データをシリアル化および逆シリアル化する
JSON (JavaScript Object Notation) は、クライアント ブラウザーと AJAX 対応の Web サービスとの間で、少量のデータを高速に交換できる効率的なデータ エンコード形式です。  
  
 ここでは JSON でエンコードされたデータに .NET 型のオブジェクトをシリアル化し、逆シリアル化、JSON 形式でデータを使用して .NET 型のインスタンスを<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>します。 この例では、ユーザー定義された `Person` 型のシリアル化と逆シリアル化を示すためにデータ コントラクトを使用します。  
  
 AJAX 対応エンドポイントで公開されたサービス操作でデータ コントラクト型を使用する場合、JSON でのシリアル化および逆シリアル化は通常 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] によって自動的に処理されます。 ただし、特定の場合においては JSON データを直接処理する必要があります。このトピックでは、このようなシナリオについて説明します。  
  
> [!NOTE]
>  サーバー上で送信応答のシリアル化中にエラーが発生した場合、または応答操作がなんらかの理由で例外をスローした場合、エラーにより応答がクライアントに戻らないことがあります。  
  
 このトピックのに基づいて、 [JSON のシリアル化](../../../../docs/framework/wcf/samples/json-serialization.md)サンプルです。  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Person のデータ コントラクトを定義するには  
  
1.  データ コントラクトを定義`Person`アタッチすることにより、 <xref:System.Runtime.Serialization.DataContractAttribute>クラスにし、 <xref:System.Runtime.Serialization.DataMemberAttribute>属性メンバーをシリアル化します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]データ コントラクトを参照してください[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)します。  
  
    ```  
    [DataContract]  
        internal class Person  
        {  
            [DataMember]  
            internal string name;  
  
            [DataMember]  
            internal int age;  
        }  
    ```  
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>Person 型のインスタンスを JSON にシリアル化するには  
  
1.  `Person` 型のインスタンスを作成します。  
  
    ```  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  シリアル化、`Person`オブジェクトを使用してメモリ ストリームを<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>します。  
  
    ```  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  使用して、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A>に JSON データをストリームに書き込みます。  
  
    ```  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  JSON の出力を表示します。  
  
    ```  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>JSON から Person 型のインスタンスに逆シリアル化するには  
  
1.  新しいインスタンスに、JSON エンコードされたデータを逆シリアル化`Person`を使用して、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A>のメソッド、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>します。  
  
    ```  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  結果を表示します。  
  
    ```  
    Console.Write("Deserialized back, got name=");  
    Console.Write(p2.name);  
    Console.Write(", age=");  
    Console.WriteLine(p2.age);  
    ```  
  
## <a name="example"></a>例  
  
```  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
  
```  
  
> [!NOTE]
>  JSON シリアライザーは、次のサンプル コードに示すように、データ コントラクターの複数のメンバーが同じ名前である場合、シリアル化例外をスローします。  
  
```  
[DataContract]  
public class TestDuplicateDataBase  
{  
    [DataMember]  
    public int field1 = 123;  
}  
[DataContract]  
public class TestDuplicateDataDerived : TestDuplicateDataBase  
{  
    [DataMember]  
    public new int field1 = 999;  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [スタンドアロン JSON のシリアル化](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)   
 [JSON およびその他のデータ転送形式をサポートします。](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)