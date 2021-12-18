# Trie-leetcode-implement

```cpp
struct Node{
    bool flag = false;
    Node* links[26];

    bool ithas(char ch){
        if(links[ch-'a']!=NULL){
            return true;
        }
        return false;
    }
    
    void attach(char ch , Node* node){
        links[ch-'a'] = node;
    }

    Node* get(char ch){
        return links[ch-'a'];
    }
    
    void setEnd(){
        flag = true;
    }
    
    bool isEnd(){
        return flag;
    }
};

// ----------------------------------------------

class Trie {
    Node* root;
public:
    Trie() {
        root = new Node();
    }
    
    
    /// for inserting node
    void insert(string word) {  
        Node* node = root;
        for(int i=0;i<word.size();i++){
            if(node->ithas(word[i])==false){
                node->attach(word[i],new Node());
            }
            // moves to new reference trie
            node = node->get(word[i]);
        }
        
        node->setEnd();
        
    }
    
    
    
    bool search(string word) {
        Node* node = root;
        
        for(int i=0;i<word.size();i++){
            if(node->ithas(word[i])==false){
                return false;
            }
            
            node = node->get(word[i]);
        }
        
        if(node->isEnd()==true){
            return true;
        }
        return false;
    }
    
    bool startsWith(string prefix) {
        Node *node = root;
        
        for(int i=0;i<prefix.size();i++){
            if(node->ithas(prefix[i])==false){
                return false;
            }
            node=node->get(prefix[i]);
        }
        
        return true;
    }
    
};

```
