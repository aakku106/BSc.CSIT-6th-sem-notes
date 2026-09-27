---
{"dg-publish":true,"permalink":"/cdc/lab/cdc-lab-all/","noteIcon":"","dg-note-properties":{"Subject":"[[CDC]]"}}
---

# CDC Lab Codes — Concise (Paper-Writing Style)

---

## Lab 1: Valid Comment Checker

```c
#include<stdio.h>
#include<string.h>
int main()
{
    char c[30]; int a=0,i;
    printf("Enter comment: ");
    gets(c);
    if(c[0]=='/' && c[1]=='/')
        printf("It is a comment");
    else if(c[0]=='/' && c[1]=='*')
    {
        for(i=2;c[i]!='\0';i++)
            if(c[i]=='*' && c[i+1]=='/') { a=1; break; }
        printf(a ? "It is a comment" : "It is not a comment");
    }
    else
        printf("It is not a comment");
    return 0;
}
```

---

## Lab 2: Recognize Strings under a*, a*b+, abb

```c
#include<stdio.h>
#include<stdlib.h>
int main()
{
    char s[20], c; int state=0, i=0;
    printf("Enter a string: ");
    gets(s);
    while(s[i]!='\0')
    {
        c=s[i++];
        switch(state)
        {
            case 0: state = (c=='a')?1:(c=='b')?2:6; break;
            case 1: state = (c=='a')?3:(c=='b')?4:6; break;
            case 2: state = (c=='b')?2:6; break;
            case 3: state = (c=='a')?3:(c=='b')?2:6; break;
            case 4: state = (c=='b')?5:6; break;
            case 5: state = (c=='b')?2:6; break;
        }
        if(state==6) { printf("%s is not recognized", s); return 0; }
    }
    if(state==1) printf("%s accepted under 'a'", s);
    else if(state==2||state==4) printf("%s accepted under 'a*b+'", s);
    else if(state==5) printf("%s accepted under 'abb'", s);
    return 0;
}
```

---

## Lab 3: Valid Identifier Checker

```c
#include<stdio.h>
#include<ctype.h>
int main()
{
    char a[10]; int flag=1, i=1;
    printf("Enter an identifier: ");
    gets(a);
    if(!(isalpha(a[0]) || a[0]=='_')) flag=0;
    while(flag && a[i]!='\0')
    {
        if(!isalnum(a[i]) && a[i]!='_') flag=0;
        i++;
    }
    printf(flag ? "Valid identifier" : "Not a valid identifier");
    return 0;
}
```

---

## Lab 4: Lexical Analyzer

```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int isKeyword(char b[])
{
    char kw[32][10]={"auto","break","case","char","const","continue","default","do",
    "double","else","enum","extern","float","for","goto","if","int","long","register",
    "return","short","signed","sizeof","static","struct","switch","typedef","union",
    "unsigned","void","volatile","while"};
    int i;
    for(i=0;i<32;i++) if(strcmp(kw[i],b)==0) return 1;
    return 0;
}
int main()
{
    char ch, buf[15], op[]="+-*/%=";
    FILE *fp=fopen("aa.txt","r");
    int i,j=0;
    if(!fp){ printf("error opening file"); return 0; }
    while((ch=fgetc(fp))!=EOF)
    {
        for(i=0;i<6;i++) if(ch==op[i]) printf("%c is operator\n",ch);
        if(isalnum(ch)) buf[j++]=ch;
        else if((ch==' '||ch=='\n') && j!=0)
        {
            buf[j]='\0'; j=0;
            printf(isKeyword(buf) ? "%s is keyword\n" : "%s is identifier\n", buf);
        }
    }
    fclose(fp);
    return 0;
}
```

---

## Lab 5: FIRST of a Grammar

```c
#include<stdio.h>
#include<ctype.h>
int n;
char prod[10][10], result[20];
void addTo(char R[], char v)
{
    int k; for(k=0;R[k]!='\0';k++) if(R[k]==v) return;
    R[k]=v; R[k+1]='\0';
}
void FIRST(char *R, char c)
{
    int i,j,k; char sub[20]; int eps;
    R[0]='\0';
    if(!isupper(c)) { addTo(R,c); return; }
    for(i=0;i<n;i++)
    {
        if(prod[i][0]==c)
        {
            if(prod[i][2]=='$') addTo(R,'$');
            else
            {
                j=2;
                while(prod[i][j]!='\0')
                {
                    eps=0; FIRST(sub, prod[i][j]);
                    for(k=0;sub[k]!='\0';k++)
                    {
                        addTo(R, sub[k]);
                        if(sub[k]=='$') eps=1;
                    }
                    if(!eps) break;
                    j++;
                }
            }
        }
    }
}
int main()
{
    int i; char ch, choice;
    printf("No. of productions: "); scanf(" %d", &n);
    for(i=0;i<n;i++){ printf("Production %d: ",i+1); scanf(" %s", prod[i]); }
    do
    {
        printf("Find FIRST of: "); scanf(" %c", &ch);
        FIRST(result, ch);
        printf("FIRST(%c) = { ", ch);
        for(i=0;result[i]!='\0';i++) printf("%c ", result[i]);
        printf("}\n");
        printf("Continue(y/n)? "); scanf(" %c", &choice);
    } while(choice=='y'||choice=='Y');
    return 0;
}
```

---

## Lab 6: FOLLOW of a Grammar

```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int n; char a[10][10], result[20];
void addTo(char R[], char v)
{
    int k; for(k=0;R[k]!='\0';k++) if(R[k]==v) return;
    R[k]=v; R[k+1]='\0';
}
void first(char *R, char c);
void follow(char *R, char c)
{
    int i,j,k; char sub[20];
    R[0]='\0';
    if(a[0][0]==c) addTo(R,'$');
    for(i=0;i<n;i++)
        for(j=2;j<(int)strlen(a[i]);j++)
            if(a[i][j]==c)
            {
                if(a[i][j+1]!='\0') first(sub, a[i][j+1]);
                else if(c!=a[i][0]) follow(sub, a[i][0]);
                for(k=0;sub[k]!='\0';k++) addTo(R, sub[k]);
            }
}
void first(char *R, char c)
{
    int k;
    if(!isupper(c) && c!='#') { addTo(R,c); return; }
    for(k=0;k<n;k++)
        if(a[k][0]==c)
        {
            if(a[k][2]=='#') follow(R, a[k][0]);
            else if(!isupper(a[k][2])) addTo(R, a[k][2]);
            else first(R, a[k][2]);
        }
}
int main()
{
    int i, choice; char c;
    printf("No. of productions: "); scanf("%d", &n);
    for(i=0;i<n;i++) scanf("%s", a[i]);
    do
    {
        printf("Find FOLLOW of: "); scanf(" %c", &c);
        follow(result, c);
        printf("FOLLOW(%c) = { ", c);
        for(i=0;result[i]!='\0';i++) printf("%c ", result[i]);
        printf("}\n");
        printf("Continue(1/0)? "); scanf("%d", &choice);
    } while(choice==1);
    return 0;
}
```

---

## Lab 7: LL(1) Parsing (Table-Driven)

```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
char s[20], stack[20];
int main()
{
    char m[5][6][4]={"tb"," "," ","tb"," "," "," ","+tb"," "," ","n","n",
    "fc"," "," ","fc"," "," "," ","n","*fc"," "," ","n","n",
    "i"," "," ","(e)"," "," "};
    int size[5][6]={2,0,0,2,0,0, 0,3,0,0,1,1, 2,0,0,2,0,0,
                     0,1,3,0,1,1, 1,0,0,3,0,0};
    int i,j,k,n,str1,str2;
    printf("Enter input string: "); scanf("%s", s);
    strcat(s,"$");
    n=strlen(s);
    stack[0]='$'; stack[1]='e'; i=1; j=0;
    printf("Stack\t\tInput\n");
    while(stack[i]!='$' && s[j]!='$')
    {
        if(stack[i]==s[j]) { i--; j++; }
        switch(stack[i]) { case 'e':str1=0;break; case 'b':str1=1;break;
            case 't':str1=2;break; case 'c':str1=3;break; case 'f':str1=4;break; }
        switch(s[j]) { case 'i':str2=0;break; case '+':str2=1;break;
            case '*':str2=2;break; case '(':str2=3;break;
            case ')':str2=4;break; case '$':str2=5;break; }
        if(m[str1][str2][0]=='\0') { printf("ERROR"); exit(0); }
        else if(m[str1][str2][0]=='n') i--;
        else if(m[str1][str2][0]=='i') stack[i]='i';
        else
        {
            for(k=size[str1][str2]-1;k>=0;k--) { stack[i]=m[str1][str2][k]; i++; }
            i--;
        }
        for(k=0;k<=i;k++) printf("%c",stack[k]);
        printf("\t\t");
        for(k=j;k<=n;k++) printf("%c",s[k]);
        printf("\n");
    }
    printf("SUCCESS");
    return 0;
}
```

---

## Lab 8: Shift Reduce Parser

```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
char ip[15], stack[15]; int ip_ptr=0, st_ptr=0, len;

void check()
{
    char t = stack[st_ptr];
    if(t=='a' || t=='b')
    {
        stack[st_ptr]='E';
        printf("$%s\t\t%s\t\tE->%c\n", stack, ip+ip_ptr, t);
    }
    if(strcmp(stack,"E+E")==0 || strcmp(stack,"E*E")==0 || strcmp(stack,"E/E")==0)
    {
        char op = stack[1];
        strcpy(stack, "E"); st_ptr=0;
        printf("$%s\t\t%s\t\tE->E%cE\n", stack, ip+ip_ptr, op);
    }
    if(strcmp(stack,"E")==0 && ip_ptr==len)
    {
        printf("$%s\t\t%s\t\tACCEPT\n", stack, ip+ip_ptr);
        exit(0);
    }
}
int main()
{
    int i;
    printf("Grammar: E->E+E | E*E | E/E | a | b\n");
    printf("Enter input string: "); scanf("%s", ip);
    len=strlen(ip);
    printf("Stack\t\tInput\t\tAction\n");
    for(i=0;i<len;i++)
    {
        stack[st_ptr]=ip[ip_ptr];
        stack[st_ptr+1]='\0';
        ip_ptr++;
        printf("$%s\t\t%s\t\tshift %c\n", stack, ip+ip_ptr, ip[ip_ptr-1]);
        check();
        st_ptr++;
    }
    printf("REJECT");
    return 0;
}
```

---

## Lab 9a: Intermediate Code Generation

```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
int j=0, tmpch=90;
char str[100], left[15], right[15];
struct { int pos; char op; } k[15];

void findopr()
{
    int i; char ops[]="/*+-";
    int oi;
    for(oi=0; ops[oi]; oi++)
        for(i=0;str[i]!='\0';i++)
            if(str[i]==ops[oi]) { k[j].pos=i; k[j++].op=ops[oi]; }
}
void fleft(int x)
{
    int w=0, flag=0; x--;
    while(x!=-1 && str[x]!='+' && str[x]!='*' && str[x]!='-' && str[x]!='/' && str[x]!='=')
    {
        if(str[x]!='$' && !flag) { left[w++]=str[x]; left[w]='\0'; str[x]='$'; flag=1; }
        x--;
    }
}
void fright(int x)
{
    int w=0, flag=0; x++;
    while(str[x]!='\0' && str[x]!='+' && str[x]!='*' && str[x]!='-' && str[x]!='/' && str[x]!='=')
    {
        if(str[x]!='$' && !flag) { right[w++]=str[x]; right[w]='\0'; str[x]='$'; flag=1; }
        x++;
    }
}
int main()
{
    int i;
    printf("Enter expression: "); scanf("%s", str);
    findopr();
    for(i=0;i<j;i++)
    {
        fleft(k[i].pos); fright(k[i].pos);
        str[k[i].pos] = tmpch--;
        printf("t%d := %s %c %s\n", 90-tmpch, left, k[i].op, right);
    }
    return 0;
}
```

---

## Lab 9b: Final (Target) Code Generation

```c
#include<stdio.h>
#include<string.h>
int main()
{
    char op[2], arg1[5], arg2[5], result[5];
    FILE *fp1=fopen("input.txt","r");
    FILE *fp2=fopen("output.txt","w");
    while(fscanf(fp1,"%s%s%s%s",op,arg1,arg2,result)!=EOF)
    {
        if(strcmp(op,"=")==0)
        {
            fprintf(fp2,"MOV R0,%s\n", arg1);
            fprintf(fp2,"MOV %s,R0\n", result);
            continue;
        }
        char *ins = strcmp(op,"+")==0 ? "ADD" :
                    strcmp(op,"-")==0 ? "SUB" :
                    strcmp(op,"*")==0 ? "MUL" : "DIV";
        fprintf(fp2,"MOV R0,%s\n", arg1);
        fprintf(fp2,"%s R0,%s\n", ins, arg2);
        fprintf(fp2,"MOV %s,R0\n", result);
    }
    fclose(fp1); fclose(fp2);
    return 0;
}
```

</file_text>