![image](https://github.com/Mudit-Jxin7/DSA/assets/97677133/d3aeefff-b937-4fb9-8f38-532cddeb192f)

```
void solution(string str , string ans , int count , int pos){
  
  if(pos == str.size()){
    if(count == 0) cout << ans << endl;
    else{
      cout << ans << count << endl;
    }
    return ;
  }
  
  if(count > 0) solution(str , ans + char(count) + str[pos] , 0 , pos + 1);
  else solution(str , ans + str[pos] , 0 , pos + 1);
  
  solution(str , ans , count + 1 , pos + 1);
}
