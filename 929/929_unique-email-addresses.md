@より前かそうでないかで，メールアドレスを分割せずに処理
'''C++
class Solution {
public:
    int numUniqueEmails(vector<string>& emails) {
        set<string> unique_email_set;
        for (string& email : emails) {
            string unique_email;
            bool ignored = false, before_atmark = true;
            for (char c : email) {
                if (c == '@') {
                    ignored = false;
                    before_atmark = false;
                }
                if (c == '+' && before_atmark) ignored = true;
                if (ignored) continue;
                if (c != '.' || !before_atmark) unique_email.push_back(c);
            }
            unique_email_set.insert(unique_email);
        }
        return unique_email_set.size();
    }
};
'''

@の前かそうでないかで，メールアドレスを分割して処理
```C++
class Solution {
public:
    int numUniqueEmails(vector<string>& emails) {
        set<string> unique_email_set;
        for (string& email : emails) {
            string local_name;
            for (char c : email) {
                if (c == '+' || c == '@') break;
                if (c == '.') continue;
                local_name.push_back(c);
            }
            // local_nameに@{ドメイン名}を結合して，setに挿入
            unique_email_set.insert(local_name + email.substr(email.find('@')));
        }
        return unique_email_set.size();
    }
};
```
