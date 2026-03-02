# VS_CSharp_Tip

## 비주얼 스튜디오 최근 항목 삭제

- %localappdata%\Microsoft\VisualStudio\버전 경로로 이동
- ApplicationPrivateSettings.xml 파일 삭제

## 신기한 문법

```C#
int a = 1;
int b = -1;

Console.WriteLine(Test1(a, b));
Console.WriteLine(Test2(ref a, ref b));

int Test1(int a, int b)
{
    try
    {
        if (a == 1)
            return a;
    }
    finally
    {
        a = 100;
    }

    return b;
}

ref int Test2(ref int a, ref int b)
{
    try
    {
        if (a == 1)
            return ref a;
    }
    finally
    {
        a = 100;
    }

    return ref b;
}

// 실행 결과
//  1
//  100
```

- 메서드의 try finally문에서 try안에 return 값이 있을 경우 return할 값을 캐싱해 둔 후 fianlly문이 실행된다.
- Test1은 a가 1일 때 a의 값 1을 캐싱해두고 finally에서 a의 값을 변경한 다음에 return하기에 캐싱한 1을 return한다.
- Test2는 a가 1일 때 a의 주소를 캐싱해 두고 finally에서 a의 주소를 직접 변경하여 return하기에 캐싱한 주소에 담긴 100을 return한다.
