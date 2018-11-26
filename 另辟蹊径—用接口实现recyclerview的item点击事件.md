### 通过接口将点击事件的处理转移到 Activity 中而不是在 Adapter 中显然是一种更好的方式
首先定义一个接口：
public interface OnItemClickListener{
   void onItemClick(View v, int position);
   void onItemLongClick(View v, int position); }

给我们已定义的Adapter增加OnItemClickListener类型的成员变量，并添加setter方法：

class DramaAdapter extends RecyclerView.Adapter<DramaViewHolder> {
      OnItemClickListener mListener;
      public void setOnItemClickListener(OnItemClickListener listener){
            this.mListener = listener; } }

  在onBindViewHolder（）方法中，在holder的iteamView等空间的点击或长点击事件中，调用接口
成员变量mListener的onItemClick（）或者onItemLongClick（）方法。

```
@Override public void onBindViewHolder(final DramaAdapter.DramaHolder holder, int position) {
    ··· holder.itemView.setOnClickListener(new View.OnClickListener() {
  	@Override public void onClick(View v) {
		if(mListener != null){
	mListener.onItemClick(v, position); }
	    }
	       });
	  holder.itemView.setOnLongClickListener(new View.OnLongClickListener() { @Override public boolean onLongClick(View v) {
	     if(mListener != null){
        	mListener.onItemLongClick(v, position); return true;
	    }
 return false;
           }
     });
 }

```
item中的增加和删除：
在 Adapter中是现俩个权限为public的方法供在Activity中调用：
```
// public void addItem(int p){
       Drama newOne = new Drama(R.......);
			 notifyItemInserted(p);
}
 public void removeItem(int p ){
     if(p < mDramaList.size()){
		 mDramaList.remove(p);
		 notifyItemRemoved(p);
		 }

 }
 ```
