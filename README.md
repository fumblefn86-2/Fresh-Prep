app/(tabs)/_layout.tsx


import React from "react";
import { Tabs } from "expo-router";
import { Home, ShoppingBag, CalendarClock, Leaf, User } from "lucide-react-native";
import Colors from "@/constants/colors";
import { Dimensions } from "react-native";


const { width } = Dimensions.get('window');
const iconSize = width < 375 ? 22 : 24;


export default function TabLayout() {
 return (
   <Tabs
     screenOptions={{
       tabBarActiveTintColor: Colors.light.primary,
       tabBarInactiveTintColor: Colors.light.textLight,
       tabBarStyle: {
         borderTopColor: Colors.light.border,
         height: width < 375 ? 56 : 60,
         paddingBottom: 8,
         paddingTop: 8,
       },
       headerStyle: {
         backgroundColor: "#FFFFFF",
       },
       headerShadowVisible: false,
       tabBarLabelStyle: {
         fontSize: width < 375 ? 10 : 12,
       }
     }}
   >
     <Tabs.Screen
       name="index"
       options={{
         title: "Home",
         tabBarIcon: ({ color }) => <Home size={iconSize} color={color} />,
       }}
     />
     <Tabs.Screen
       name="shop"
       options={{
         title: "Shop",
         tabBarIcon: ({ color }) => <ShoppingBag size={iconSize} color={color} />,
       }}
     />
     <Tabs.Screen
       name="subscriptions"
       options={{
         title: "Subscriptions",
         tabBarIcon: ({ color }) => <CalendarClock size={iconSize} color={color} />,
       }}
     />
     <Tabs.Screen
       name="impact"
       options={{
         title: "Impact",
         tabBarIcon: ({ color }) => <Leaf size={iconSize} color={color} />,
       }}
     />
     <Tabs.Screen
       name="profile"
       options={{
         title: "Profile",
         tabBarIcon: ({ color }) => <User size={iconSize} color={color} />,
       }}
     />
   </Tabs>
 );
}
app/(tabs)/impact.tsx
import React from 'react';
   fontWeight: '700',
   color: '#FFFFFF',
   marginBottom: 8,
 },
 bannerText: {
   fontSize: 14,
   color: '#FFFFFF',
   textAlign: 'center',
   opacity: 0.9,
 },
 statsContainer: {
   paddingHorizontal: 16,
   marginBottom: 24,
 },
 statsRow: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   marginBottom: 16,
 },
 infoSection: {
   paddingHorizontal: 16,
   marginBottom: 24,
 },
 sectionTitle: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 16,
 },
 infoCard: {
   flexDirection: 'row',
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
   marginBottom: 12,
 },
 infoIconContainer: {
   width: 48,
   height: 48,
   borderRadius: 24,
   justifyContent: 'center',
   alignItems: 'center',
   marginRight: 16,
 },
 infoContent: {
   flex: 1,
 },
 infoTitle: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
 },
 infoText: {
   fontSize: 14,
   color: Colors.light.textLight,
   lineHeight: 20,
 },
 goalSection: {
   paddingHorizontal: 16,
   marginBottom: 32,
 },
 goalCard: {
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
   marginBottom: 12,
 },
 goalProgress: {
   height: 8,
   backgroundColor: 'rgba(76, 175, 80, 0.2)',
   borderRadius: 4,
   marginBottom: 12,
   overflow: 'hidden',
 },
 goalProgressBar: {
   height: '100%',
   backgroundColor: Colors.light.primary,
   borderRadius: 4,
 },
 goalText: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 goalHighlight: {
   fontWeight: '700',
   color: Colors.light.text,
 },
});


app/(tabs)/index.tsx
import React, { useState, useEffect } from 'react';
 );
}


const styles = StyleSheet.create({
 container: {
   flex: 1,
   backgroundColor: Colors.light.background,
 },
 header: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   paddingHorizontal: 16,
   paddingVertical: 16,
 },
 welcomeText: {
   fontSize: width < 375 ? 14 : 16,
   color: Colors.light.textLight,
   fontWeight: '500',
 },
 title: {
   fontSize: headerFontSize,
   fontWeight: '700',
   color: Colors.light.text,
 },
 sectionHeader: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   paddingHorizontal: 16,
   marginTop: 24,
   marginBottom: 16,
 },
 sectionTitle: {
   fontSize: width < 375 ? 16 : 18,
   fontWeight: '700',
   color: Colors.light.text,
 },
 seeAllButton: {
   flexDirection: 'row',
   alignItems: 'center',
 },
 seeAllText: {
   fontSize: width < 375 ? 12 : 14,
   color: Colors.light.primary,
   marginRight: 4,
   fontWeight: '600',
 },
 categoriesContainer: {
   paddingHorizontal: 16,
   paddingBottom: 8,
 },
 productsGrid: {
   flexDirection: 'row',
   flexWrap: 'wrap',
   paddingHorizontal: 16,
   marginBottom: 16,
   justifyContent: 'space-between',
 },
 productItem: {
   width: '48%',
   marginBottom: 16,
 },
 sustainabilityBanner: {
   height: height * 0.15,
   marginHorizontal: 16,
   marginVertical: 16,
   borderRadius: 16,
   overflow: 'hidden',
   position: 'relative',
   marginBottom: 32,
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 8 },
   shadowOpacity: 0.3,
   shadowRadius: 12,
   elevation: 6,
 },
 sustainabilityImage: {
   ...StyleSheet.absoluteFillObject,
   backgroundColor: '#E1E1E1',
 },
 sustainabilityContent: {
   position: 'absolute',
   top: 0,
   left: 0,
   right: 0,
   bottom: 0,
   padding: 16,
   backgroundColor: 'rgba(0, 0, 0, 0.5)',
   justifyContent: 'center',
 },
 sustainabilityTitle: {
   fontSize: width < 375 ? 18 : 20,
   fontWeight: '700',
   color: '#FFFFFF',
   marginBottom: 4,
 },
 sustainabilitySubtitle: {
   fontSize: width < 375 ? 12 : 14,
   color: '#FFFFFF',
   opacity: 0.9,
 },
});


app/(tabs)/profile.tsx


import { Image } from 'expo-image';
   flexDirection: 'row',
   alignItems: 'center',
   backgroundColor: Colors.light.cardAlt,
   borderRadius: 12,
   padding: 16,
   marginHorizontal: 16,
   marginBottom: 24,
 },
 avatarContainer: {
   width: 60,
   height: 60,
   borderRadius: 30,
   backgroundColor: Colors.light.darkGreen,
   justifyContent: 'center',
   alignItems: 'center',
   marginRight: 16,
 },
 profileInfo: {
   flex: 1,
 },
 name: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
 },
 email: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 loginButtonContainer: {
   paddingHorizontal: 16,
   marginBottom: 24,
 },
 loginButton: {
   width: '100%',
 },
 section: {
   marginBottom: 24,
 },
 sectionTitle: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.darkGreen,
   paddingHorizontal: 16,
   marginBottom: 8,
 },
 menuItem: {
   flexDirection: 'row',
   alignItems: 'center',
   paddingHorizontal: 16,
   paddingVertical: 16,
   borderBottomWidth: 1,
   borderBottomColor: Colors.light.border,
 },
 menuItemText: {
   flex: 1,
   fontSize: 16,
   color: Colors.light.text,
   marginLeft: 16,
 },
 logoutButton: {
   flexDirection: 'row',
   alignItems: 'center',
   paddingHorizontal: 16,
   paddingVertical: 16,
   marginBottom: 16,
 },
 logoutText: {
   fontSize: 16,
   color: Colors.light.error,
   marginLeft: 16,
   fontWeight: '600',
 },
 versionText: {
   fontSize: 12,
   color: Colors.light.textLight,
   textAlign: 'center',
   marginBottom: 32,
 },
});


app/(tabs)/shop.tsx


import React, { useState, useEffect } from 'react';
   flex: 1,
   backgroundColor: '#FFFFFF',
 },
 header: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   paddingHorizontal: 16,
   paddingVertical: 16,
 },
 title: {
   fontSize: headerFontSize,
   fontWeight: '700',
   color: Colors.light.text,
 },
 searchContainer: {
   flexDirection: 'row',
   alignItems: 'center',
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   marginHorizontal: 16,
   marginBottom: 16,
   paddingHorizontal: 12,
   height: width < 375 ? 44 : 48,
 },
 searchIcon: {
   marginRight: 8,
 },
 searchInput: {
   flex: 1,
   height: '100%',
   fontSize: width < 375 ? 14 : 16,
   color: Colors.light.text,
 },
 clearButton: {
   padding: 4,
 },
 categoriesContainer: {
   paddingHorizontal: 16,
   paddingBottom: 16,
 },
 categoryChip: {
   paddingHorizontal: 16,
   paddingVertical: 8,
   borderRadius: 20,
   backgroundColor: Colors.light.card,
   marginRight: 8,
   minWidth: 80,
   maxWidth: 120,
 },
 selectedCategoryChip: {
   backgroundColor: Colors.light.primary,
 },
 categoryChipText: {
   fontSize: width < 375 ? 12 : 14,
   color: Colors.light.text,
   textAlign: 'center',
 },
 selectedCategoryChipText: {
   color: '#FFFFFF',
   fontWeight: '600',
 },
 productsContainer: {
   flex: 1,
   paddingHorizontal: 16,
   paddingBottom: 24,
 },
 productsGrid: {
   flexDirection: 'row',
   flexWrap: 'wrap',
   justifyContent: 'space-between',
 },
 productItem: {
   width: '48%',
   marginBottom: 16,
 },
});


app/(tabs)/subscriptions.tsx


import React from 'react';
import { StyleSheet, Text, View, ScrollView, Pressable, SafeAreaView } from 'react-native';
import { useRouter } from 'expo-router';
import { Plus, CalendarClock } from 'lucide-react-native';
import Colors from '@/constants/colors';
import { useUserStore } from '@/store/user-store';
import SubscriptionCard from '@/components/SubscriptionCard';
import EmptyState from '@/components/EmptyState';


export default function SubscriptionsScreen() {
 const router = useRouter();
 const subscriptions = useUserStore((state) => state.subscriptions);
  const activeSubscriptions = subscriptions.filter(sub => sub.isActive);
 const inactiveSubscriptions = subscriptions.filter(sub => !sub.isActive);


 const handleCreateSubscription = () => {
   router.push('/create-subscription');
 };


 return (
   <SafeAreaView style={styles.container}>
     {/* Header */}
     <View style={styles.header}>
       <Text style={styles.title}>Subscriptions</Text>
       <Pressable style={styles.addButton} onPress={handleCreateSubscription}>
         <Plus size={20} color="#FFFFFF" />
       </Pressable>
     </View>


     {subscriptions.length > 0 ? (
       <ScrollView
         style={styles.subscriptionsContainer}
         showsVerticalScrollIndicator={false}
       >
         {/* Active Subscriptions */}
         <View style={styles.activeSection}>
           <Text style={styles.sectionTitle}>Active Subscriptions</Text>
           {activeSubscriptions.length > 0 ? (
             activeSubscriptions.map(subscription => (
               <SubscriptionCard
                 key={subscription.id}
                 subscription={subscription}
               />
             ))
           ) : (
             <Text style={styles.emptyMessage}>No active subscriptions</Text>
           )}
         </View>


         {/* Inactive Subscriptions */}
         <View style={styles.inactiveSection}>
           <Text style={styles.sectionTitle}>Paused Subscriptions</Text>
           {inactiveSubscriptions.length > 0 ? (
             inactiveSubscriptions.map(subscription => (
               <SubscriptionCard
                 key={subscription.id}
                 subscription={subscription}
               />
             ))
           ) : (
             <Text style={styles.emptyMessage}>No paused subscriptions</Text>
           )}
         </View>
       </ScrollView>
     ) : (
       <EmptyState
         icon={<CalendarClock size={32} color={Colors.light.primary} />}
         title="No Subscriptions Yet"
         message="Subscribe to your favorite products and have them delivered regularly."
         buttonTitle="Create Subscription"
         onButtonPress={handleCreateSubscription}
       />
     )}
   </SafeAreaView>
 );
}


const styles = StyleSheet.create({
 container: {
   flex: 1,
   backgroundColor: '#FFFFFF',
 },
 header: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   paddingHorizontal: 16,
   paddingVertical: 16,
 },
 title: {
   fontSize: 24,
   fontWeight: '700',
   color: Colors.light.text,
 },
 addButton: {
   width: 40,
   height: 40,
   borderRadius: 20,
   backgroundColor: Colors.light.primary,
   justifyContent: 'center',
   alignItems: 'center',
 },
 subscriptionsContainer: {
   flex: 1,
   paddingHorizontal: 16,
 },
 activeSection: {
   marginBottom: 24,
 },
 inactiveSection: {
   marginBottom: 24,
 },
 sectionTitle: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 16,
 },
 emptyMessage: {
   fontSize: 14,
   color: Colors.light.textLight,
   fontStyle: 'italic',
   marginBottom: 16,
 },
});


app/category/[id].tsx


import { StyleSheet, Text, View, ScrollView, Dimensions, SafeAreaView } from 'react-native';
                     <AnimatedProductCard product={product} index={index} />
                   </View>
                 ))}
               </View>
             ) : (
               <EmptyState
                 icon={<ShoppingBag size={32} color={Colors.light.primary} />}
                 title="No products found"
                 message="We don't have any products in this category at the moment."
                 buttonTitle="Browse Other Categories"
                 onButtonPress={handleShopMore}
               />
             )}
           </View>
         </ScrollView>
       </PageTransition>
     </SafeAreaView>
   </>
 );
}


const styles = StyleSheet.create({
 container: {
   flex: 1,
   backgroundColor: Colors.light.background,
 },
 headerImageContainer: {
   height: 180,
   position: 'relative',
   marginBottom: 16,
 },
 headerImage: {
   width: '100%',
   height: '100%',
 },
 headerOverlay: {
   ...StyleSheet.absoluteFillObject,
   backgroundColor: 'rgba(0, 0, 0, 0.4)',
   justifyContent: 'flex-end',
   padding: 16,
 },
 title: {
   fontSize: headerFontSize,
   fontWeight: '700',
   color: '#FFFFFF',
   marginBottom: 4,
 },
 count: {
   fontSize: width < 375 ? 14 : 16,
   color: 'rgba(255, 255, 255, 0.8)',
 },
 productsContainer: {
   paddingHorizontal: 16,
   paddingBottom: 24,
 },
 productsGrid: {
   flexDirection: 'row',
   flexWrap: 'wrap',
   justifyContent: 'space-between',
 },
 productItem: {
   width: '48%',
   marginBottom: 16,
 },
 notFound: {
   flex: 1,
   justifyContent: 'center',
   alignItems: 'center',
   padding: 16,
 },
 notFoundText: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
 },
});


app/product/[id].tsx


import * as Haptics from 'expo-haptics';
   borderBottomColor: Colors.light.borderLight,
 },
 sectionTitle: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 16,
 },
 impactRow: {
   flexDirection: 'row',
   justifyContent: 'space-around',
   marginBottom: 16,
 },
 impactItem: {
   flexDirection: 'row',
   alignItems: 'center',
 },
 impactIconContainer: {
   width: 44,
   height: 44,
   borderRadius: 22,
   justifyContent: 'center',
   alignItems: 'center',
   marginRight: 12,
 },
 impactValue: {
   fontSize: 16,
   fontWeight: '700',
   color: Colors.light.text,
 },
 impactLabel: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 learnMoreButton: {
   flexDirection: 'row',
   alignItems: 'center',
   justifyContent: 'center',
   marginTop: 8,
 },
 learnMoreText: {
   fontSize: 14,
   color: Colors.light.primary,
   marginRight: 4,
   fontWeight: '500',
 },
 nutritionContainer: {
   padding: 20,
   borderBottomWidth: 1,
   borderBottomColor: Colors.light.borderLight,
 },
 nutritionRow: {
   flexDirection: 'row',
   justifyContent: 'space-between',
 },
 nutritionItem: {
   alignItems: 'center',
   backgroundColor: Colors.light.cardAlt,
   paddingVertical: 12,
   paddingHorizontal: 16,
   borderRadius: 12,
   minWidth: 70,
 },
 nutritionValue: {
   fontSize: 16,
   fontWeight: '700',
   color: Colors.light.text,
 },
 nutritionLabel: {
   fontSize: 14,
   color: Colors.light.textLight,
   marginTop: 4,
 },
 actionContainer: {
   flexDirection: 'row',
   padding: 16,
   borderTopWidth: 1,
   borderTopColor: Colors.light.borderLight,
   backgroundColor: Colors.light.background,
   position: 'absolute',
   bottom: 0,
   left: 0,
   right: 0,
   zIndex: 10,
   shadowColor: '#000',
   shadowOffset: { width: 0, height: -4 },
   shadowOpacity: 0.1,
   shadowRadius: 8,
   elevation: 8,
 },
 addButton: {
   flex: 1,
   marginRight: 8,
 },
 buyButton: {
   flex: 1,
   marginLeft: 8,
 },
});


app/subscription/[id].tsx


import React, { useState, useEffect } from 'react';
   padding: 12,
   marginTop: 8,
   marginBottom: 16,
 },
 addProductText: {
   fontSize: 16,
   color: Colors.light.primary,
   fontWeight: '600',
   marginLeft: 8,
 },
 productSelectorContainer: {
   paddingBottom: 16,
 },
 productSelectorItem: {
   width: 120,
   marginRight: 12,
   backgroundColor: '#FFFFFF',
   borderRadius: 8,
   overflow: 'hidden',
   borderWidth: 1,
   borderColor: Colors.light.border,
 },
 productSelectorImage: {
   width: '100%',
   height: 80,
   backgroundColor: '#E1E1E1',
 },
 productSelectorName: {
   fontSize: 12,
   fontWeight: '600',
   color: Colors.light.text,
   padding: 8,
   paddingBottom: 4,
   height: 40,
 },
 productSelectorPrice: {
   fontSize: 12,
   fontWeight: '700',
   color: Colors.light.primary,
   paddingHorizontal: 8,
   paddingBottom: 8,
 },
 productSelectorAddButton: {
   position: 'absolute',
   bottom: 8,
   right: 8,
   width: 24,
   height: 24,
   borderRadius: 12,
   backgroundColor: Colors.light.primary,
   justifyContent: 'center',
   alignItems: 'center',
 },
 totalContainer: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   paddingTop: 16,
   borderTopWidth: 1,
   borderTopColor: Colors.light.border,
 },
 totalLabel: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.text,
 },
 totalAmount: {
   fontSize: 18,
   fontWeight: '700',
   color: Colors.light.primary,
 },
 actionsSection: {
   padding: 16,
 },
 actionButton: {
   marginBottom: 12,
 },
 deleteButton: {
   borderColor: Colors.light.error,
 },
 deleteButtonText: {
   color: Colors.light.error,
 },
 notFound: {
   flex: 1,
   justifyContent: 'center',
   alignItems: 'center',
   padding: 16,
 },
 notFoundText: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 16,
 },
});


app/_layout.tsx


import FontAwesome from "@expo/vector-icons/FontAwesome";
     />
     <Stack.Screen
       name="cart"
       options={{
         title: "Shopping Cart",
         headerBackTitle: "Back",
       }}
     />
     <Stack.Screen
       name="checkout"
       options={{
         title: "Checkout",
         headerBackTitle: "Back",
       }}
     />
     <Stack.Screen
       name="order-confirmation"
       options={{
         title: "Order Confirmed",
         headerBackTitle: "Back",
         gestureEnabled: false,
       }}
     />
     <Stack.Screen
       name="subscription/[id]"
       options={{
         title: "Subscription Details",
         headerBackTitle: "Back",
       }}
     />
     <Stack.Screen
       name="create-subscription"
       options={{
         title: "Create Subscription",
         headerBackTitle: "Back",
       }}
     />
     <Stack.Screen
       name="about"
       options={{
         title: "About Us",
         headerBackTitle: "Back",
       }}
     />
     <Stack.Screen
       name="login"
       options={{
         title: "Sign In",
         headerBackTitle: "Back",
         presentation: "card",
       }}
     />
     <Stack.Screen
       name="register"
       options={{
         title: "Create Account",
         headerBackTitle: "Back",
         presentation: "card",
       }}
     />
     <Stack.Screen
       name="notification-settings"
       options={{
         title: "Notification Settings",
         headerBackTitle: "Back",
       }}
     />
   </Stack>
 );
}


app/+not-found.tsx
import { Link, Stack } from "expo-router";
import { StyleSheet, Text, View } from "react-native";


export default function NotFoundScreen() {
 return (
   <>
     <Stack.Screen options={{ title: "Oops!" }} />
     <View style={styles.container}>
       <Text style={styles.title}>This screen doesn't exist.</Text>


       <Link href="/" style={styles.link}>
         <Text style={styles.linkText}>Go to home screen!</Text>
       </Link>
     </View>
   </>
 );
}


const styles = StyleSheet.create({
 container: {
   flex: 1,
   alignItems: "center",
   justifyContent: "center",
   padding: 20,
 },
 title: {
   fontSize: 20,
   fontWeight: "bold",
 },
 link: {
   marginTop: 15,
   paddingVertical: 15,
 },
 linkText: {
   fontSize: 14,
   color: "#2e78b7",
 },
});


app/about.tsx


import React from 'react';
   shadowOffset: { width: 0, height: 1 },
   shadowOpacity: 0.1,
   shadowRadius: 2,
   elevation: 2,
 },
 featureIconContainer: {
   width: 48,
   height: 48,
   borderRadius: 24,
   backgroundColor: 'rgba(76, 175, 80, 0.1)',
   justifyContent: 'center',
   alignItems: 'center',
   marginRight: 16,
 },
 featureContent: {
   flex: 1,
 },
 featureTitle: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
 },
 featureText: {
   fontSize: 14,
   color: Colors.light.textLight,
   lineHeight: 20,
 },
 teamGrid: {
   flexDirection: 'row',
   justifyContent: 'space-around',
   marginTop: 16,
   marginBottom: 24,
 },
 teamMember: {
   alignItems: 'center',
   marginBottom: 24,
   width: width / 2 - 32,
 },
 teamAvatarContainer: {
   width: 80,
   height: 80,
   borderRadius: 40,
   backgroundColor: Colors.light.primary,
   justifyContent: 'center',
   alignItems: 'center',
   marginBottom: 12,
 },
 teamName: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
   textAlign: 'center',
 },
 teamRole: {
   fontSize: 16,
   color: Colors.light.textLight,
   textAlign: 'center',
 },
 contactTitle: {
   fontSize: 18,
   fontWeight: '700',
   color: Colors.light.text,
   marginBottom: 8,
 },
 contactText: {
   fontSize: 16,
   color: Colors.light.text,
   lineHeight: 24,
   marginBottom: 32,
 },
});


app/cart.tsx


import React, { useState } from 'react';
 itemUnit: {
   fontSize: width < 375 ? 10 : 12,
   color: Colors.light.textLight,
   marginBottom: 8,
 },
 itemActions: {
   flexDirection: 'row',
   alignItems: 'center',
 },
 removeButton: {
   marginLeft: 12,
   padding: 4,
 },
 itemPrice: {
   fontSize: width < 375 ? 14 : 16,
   fontWeight: '700',
   color: Colors.light.text,
   marginLeft: 12,
   alignSelf: 'center',
 },
 summaryContainer: {
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
   margin: 16,
   marginTop: 0,
 },
 summaryTitle: {
   fontSize: width < 375 ? 16 : 18,
   fontWeight: '700',
   color: Colors.light.text,
   marginBottom: 16,
 },
 summaryRow: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   marginBottom: 12,
 },
 summaryLabel: {
   fontSize: width < 375 ? 12 : 14,
   color: Colors.light.textLight,
 },
 summaryValue: {
   fontSize: width < 375 ? 12 : 14,
   fontWeight: '600',
   color: Colors.light.text,
 },
 divider: {
   height: 1,
   backgroundColor: Colors.light.border,
   marginVertical: 12,
 },
 totalLabel: {
   fontSize: width < 375 ? 14 : 16,
   fontWeight: '700',
   color: Colors.light.text,
 },
 totalValue: {
   fontSize: width < 375 ? 16 : 18,
   fontWeight: '700',
   color: Colors.light.primary,
 },
 footer: {
   borderTopWidth: 1,
   borderTopColor: Colors.light.border,
   padding: 16,
   backgroundColor: '#FFFFFF',
 },
 checkoutButton: {
   width: '100%',
 },
});


app/checkout.tsx


import React, { useState, useEffect } from 'react';
 },
 paymentIcon: {
   marginRight: 12,
 },
 paymentOptionText: {
   fontSize: 16,
   color: Colors.light.text,
 },
 applePayIcon: {
   width: 24,
   height: 24,
   marginRight: 12,
 },
 applePayText: {
   color: '#FFF',
   fontSize: 14,
   fontWeight: '600',
 },
 paypalIcon: {
   backgroundColor: '#0070BA',
   paddingHorizontal: 8,
   paddingVertical: 4,
   borderRadius: 4,
   marginRight: 12,
 },
 paypalText: {
   color: '#FFF',
   fontSize: 14,
   fontWeight: '600',
 },
 radioButton: {
   width: 20,
   height: 20,
   borderRadius: 10,
   borderWidth: 2,
   borderColor: Colors.light.border,
   justifyContent: 'center',
   alignItems: 'center',
   marginRight: 12,
 },
 radioButtonSelected: {
   borderColor: Colors.light.primary,
 },
 radioButtonInner: {
   width: 10,
   height: 10,
   borderRadius: 5,
   backgroundColor: Colors.light.primary,
 },
 optionIcon: {
   marginRight: 12,
 },
 summaryCard: {
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
 },
 summaryRow: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   marginBottom: 12,
 },
 summaryLabel: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 summaryValue: {
   fontSize: 14,
   fontWeight: '600',
   color: Colors.light.text,
 },
 divider: {
   height: 1,
   backgroundColor: Colors.light.border,
   marginVertical: 12,
 },
 totalLabel: {
   fontSize: 16,
   fontWeight: '700',
   color: Colors.light.text,
 },
 totalValue: {
   fontSize: 18,
   fontWeight: '700',
   color: Colors.light.primary,
 },
 footer: {
   borderTopWidth: 1,
   borderTopColor: Colors.light.border,
   padding: 16,
   backgroundColor: '#FFFFFF',
 },
 placeOrderButton: {
   width: '100%',
 },
 applePayButton: {
   width: '100%',
 },
});


app/create-subscription.tsx


import React, { useState } from 'react';
 },
 selectedProductPrice: {
   fontSize: 16,
   fontWeight: '700',
   color: Colors.light.text,
 },
 totalContainer: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   paddingTop: 16,
   borderTopWidth: 1,
   borderTopColor: Colors.light.border,
 },
 totalLabel: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.text,
 },
 totalAmount: {
   fontSize: 18,
   fontWeight: '700',
   color: Colors.light.primary,
 },
 categoriesContainer: {
   flexDirection: 'row',
   marginBottom: 16,
 },
 categoryChip: {
   paddingHorizontal: 16,
   paddingVertical: 8,
   borderRadius: 20,
   backgroundColor: Colors.light.card,
   marginRight: 8,
 },
 selectedCategoryChip: {
   backgroundColor: Colors.light.primary,
 },
 categoryChipText: {
   fontSize: 14,
   color: Colors.light.text,
 },
 selectedCategoryChipText: {
   color: '#FFFFFF',
   fontWeight: '600',
 },
 productsGrid: {
   flexDirection: 'row',
   flexWrap: 'wrap',
   justifyContent: 'space-between',
 },
 productCard: {
   width: '48%',
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   overflow: 'hidden',
   marginBottom: 16,
 },
 productImage: {
   width: '100%',
   height: 120,
   backgroundColor: '#E1E1E1',
 },
 productInfo: {
   padding: 12,
   position: 'relative',
 },
 productName: {
   fontSize: 14,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
   paddingRight: 36,
 },
 productPrice: {
   fontSize: 14,
   fontWeight: '700',
   color: Colors.light.text,
 },
 addButton: {
   position: 'absolute',
   right: 12,
   bottom: 12,
   width: 28,
   height: 28,
   borderRadius: 14,
   backgroundColor: Colors.light.primary,
   justifyContent: 'center',
   alignItems: 'center',
 },
 footer: {
   padding: 16,
   borderTopWidth: 1,
   borderTopColor: Colors.light.border,
   backgroundColor: '#FFFFFF',
 },
});


app/error-boundary.tsx


import React from 'react';
   sendErrorToIframeParent(event.reason);
 }, true);


 const originalConsoleError = console.error;
 console.error = (...args) => {
   sendErrorToIframeParent(args.join(' '));
   originalConsoleError.apply(console, args);
 };
}


export class ErrorBoundary extends React.Component<Props, State> {
 constructor(props: Props) {
   super(props);
   this.state = { hasError: false, error: null };
 }


 static getDerivedStateFromError(error: Error) {
   return { hasError: true, error };
 }


 componentDidCatch(error: Error, errorInfo: React.ErrorInfo) {
   sendErrorToIframeParent(error, errorInfo);
   if (this.props.onError) {
     this.props.onError(error, errorInfo);
   }
 }


 render() {
   if (this.state.hasError) {
     return (
       <View style={styles.container}>
         <View style={styles.content}>
           <Text style={styles.title}>Something went wrong</Text>
           <Text style={styles.subtitle}>{this.state.error?.message}</Text>
           {Platform.OS !== 'web' && (
             <Text style={styles.description}>
               Please check your device logs for more details.
             </Text>
           )}
         </View>
       </View>
     );
   }


   return this.props.children;
 }
}


const styles = StyleSheet.create({
 container: {
   flex: 1,
   backgroundColor: '#fff',
 },
 content: {
   flex: 1,
   alignItems: 'center',
   justifyContent: 'center',
   padding: 20,
 },
 title: {
   fontSize: 36,
   textAlign: 'center',
   fontWeight: 'bold',
   marginBottom: 8,
 },
 subtitle: {
   fontSize: 14,
   color: '#666',
   marginBottom: 12,
   textAlign: 'center',
 },
 description: {
   fontSize: 14,
   color: '#666',
   textAlign: 'center',
   marginTop: 8,
 },
});


export default ErrorBoundary;


app/impact.tsx


import { Leaf, Droplets, Wind, Info } from 'lucide-react-native';
   gap: 12,
 },
 infoSection: {
   paddingHorizontal: 16,
   marginBottom: 24,
 },
 sectionTitle: {
   fontSize: 18,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 16,
 },
 infoCard: {
   flexDirection: 'row',
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
   marginBottom: 12,
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 2 },
   shadowOpacity: 0.1,
   shadowRadius: 4,
   elevation: 2,
 },
 infoIconContainer: {
   width: 48,
   height: 48,
   borderRadius: 24,
   backgroundColor: 'rgba(76, 175, 80, 0.1)',
   justifyContent: 'center',
   alignItems: 'center',
   marginRight: 16,
 },
 infoContent: {
   flex: 1,
 },
 infoTitle: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
 },
 infoText: {
   fontSize: 14,
   color: Colors.light.textLight,
   lineHeight: 20,
 },
 goalSection: {
   paddingHorizontal: 16,
   marginBottom: 32,
 },
 goalCard: {
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
   marginBottom: 12,
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 2 },
   shadowOpacity: 0.1,
   shadowRadius: 4,
   elevation: 2,
 },
 goalProgress: {
   height: 8,
   backgroundColor: 'rgba(76, 175, 80, 0.2)',
   borderRadius: 4,
   marginBottom: 12,
   overflow: 'hidden',
 },
 goalProgressBar: {
   height: '100%',
   backgroundColor: Colors.light.primary,
   borderRadius: 4,
 },
 goalText: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 goalHighlight: {
   fontWeight: '700',
   color: Colors.light.text,
 },
});


app/login.tsx


 Pressable,
 inputIcon: {
   marginRight: 12,
 },
 input: {
   flex: 1,
   height: '100%',
   fontSize: 16,
   color: Colors.light.text,
 },
 eyeIcon: {
   padding: 8,
 },
 forgotPasswordContainer: {
   alignSelf: 'flex-end',
   marginBottom: 24,
 },
 forgotPasswordText: {
   fontSize: 14,
   color: Colors.light.darkGreen,
   fontWeight: '600',
 },
 loginButton: {
   height: 56,
   borderRadius: 12,
 },
 dividerContainer: {
   flexDirection: 'row',
   alignItems: 'center',
   marginBottom: 24,
 },
 divider: {
   flex: 1,
   height: 1,
   backgroundColor: Colors.light.border,
 },
 dividerText: {
   fontSize: 14,
   color: Colors.light.textLight,
   marginHorizontal: 16,
 },
 socialButtonsContainer: {
   marginBottom: 24,
 },
 socialButton: {
   height: 56,
   borderRadius: 12,
   flexDirection: 'row',
   justifyContent: 'center',
   alignItems: 'center',
   marginBottom: 16,
 },
 socialButtonText: {
   fontSize: 16,
   fontWeight: '600',
 },
 socialIcon: {
   width: 24,
   height: 24,
   marginRight: 12,
 },
 registerContainer: {
   flexDirection: 'row',
   justifyContent: 'center',
   alignItems: 'center',
   marginTop: 'auto',
 },
 registerText: {
   fontSize: 14,
   color: Colors.light.textLight,
   marginRight: 8,
 },
 registerButton: {
   padding: 4,
 },
 registerButtonText: {
   fontSize: 14,
   color: Colors.light.darkGreen,
   fontWeight: '600',
 },
});


app/modal.tsx


import { StatusBar } from "expo-status-bar";
import { Platform, StyleSheet, Text, View } from "react-native";


export default function ModalScreen() {
 return (
   <View style={styles.container}>
     <Text style={styles.title}>Modal</Text>
     <View style={styles.separator} />
     <Text>This is an example modal. You can edit it in app/modal.tsx.</Text>


     {/* Use a light status bar on iOS to account for the black space above the modal */}
     <StatusBar style={Platform.OS === "ios" ? "light" : "auto"} />
   </View>
 );
}


const styles = StyleSheet.create({
 container: {
   flex: 1,
   alignItems: "center",
   justifyContent: "center",
 },
 title: {
   fontSize: 20,
   fontWeight: "bold",
 },
 separator: {
   marginVertical: 30,
   height: 1,
   width: "80%",
 },
});


app/notification-settings.tsx


           </View>
 },
 permissionTextContainer: {
   marginLeft: 16,
   flex: 1,
 },
 permissionTitle: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
 },
 permissionText: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 permissionButton: {
   backgroundColor: Colors.light.primary,
   paddingHorizontal: 16,
   paddingVertical: 8,
   borderRadius: 8,
   marginLeft: 16,
 },
 permissionButtonText: {
   color: '#FFFFFF',
   fontWeight: '600',
   fontSize: 14,
 },
 optionContainer: {
   flexDirection: 'row',
   alignItems: 'center',
   justifyContent: 'space-between',
   paddingVertical: 16,
   borderBottomWidth: 1,
   borderBottomColor: Colors.light.borderLight,
 },
 optionTextContainer: {
   flex: 1,
   marginRight: 16,
 },
 optionTitle: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
 },
 optionDescription: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 infoContainer: {
   flexDirection: 'row',
   padding: 16,
   backgroundColor: Colors.light.backgroundAlt,
   marginHorizontal: 16,
   marginVertical: 24,
   borderRadius: 12,
 },
 infoIcon: {
   marginRight: 12,
   marginTop: 2,
 },
 infoText: {
   fontSize: 14,
   color: Colors.light.textLight,
   flex: 1,
   lineHeight: 20,
 },
 buttonContainer: {
   padding: 16,
   borderTopWidth: 1,
   borderTopColor: Colors.light.border,
 },
 saveButton: {
   height: 50,
   borderRadius: 12,
 },
});




app/order-confirmation.tsx


import React, { useState, useEffect } from 'react';
 trackingImageContainer: {
   width: 100,
   height: 180,
 },
 trackingImage: {
   width: '100%',
   height: '100%',
 },
 trackingContent: {
   flex: 1,
   padding: 16,
   justifyContent: 'space-between',
 },
 trackingStep: {
   flexDirection: 'row',
   alignItems: 'center',
   height: 32,
 },
 trackingDot: {
   width: 12,
   height: 12,
   borderRadius: 6,
   backgroundColor: '#E0E0E0',
   marginRight: 12,
 },
 activeDot: {
   backgroundColor: Colors.light.primary,
 },
 trackingLine: {
   position: 'absolute',
   left: 6,
   top: 12,
   width: 1,
   height: 32,
   backgroundColor: '#E0E0E0',
   zIndex: -1,
 },
 trackingText: {
   fontSize: 14,
   color: Colors.light.textLight,
 },
 activeText: {
   color: Colors.light.text,
   fontWeight: '600',
 },
 impactContainer: {
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
 },
 impactText: {
   fontSize: 14,
   color: Colors.light.text,
   marginBottom: 16,
 },
 impactStats: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   marginBottom: 16,
 },
 impactStat: {
   alignItems: 'center',
 },
 impactValue: {
   fontSize: 18,
   fontWeight: '700',
   color: Colors.light.primary,
   marginBottom: 4,
 },
 impactLabel: {
   fontSize: 12,
   color: Colors.light.textLight,
 },
 impactButton: {
   alignItems: 'center',
   paddingVertical: 8,
 },
 impactButtonText: {
   fontSize: 14,
   color: Colors.light.primary,
   fontWeight: '600',
 },
 buttonContainer: {
   padding: 16,
   marginBottom: 16,
 },
 continueButton: {
   marginBottom: 12,
 },
 ordersButton: {
   backgroundColor: 'transparent',
 },
});


app/register.tsx


import React, { useState } from 'react';
   backgroundColor: '#FFFFFF',
 },
 keyboardAvoidingView: {
   flex: 1,
 },
 scrollContent: {
   flexGrow: 1,
   padding: 24,
 },
 header: {
   marginBottom: 32,
 },
 backButton: {
   width: 40,
   height: 40,
   borderRadius: 20,
   backgroundColor: Colors.light.cardAlt,
   justifyContent: 'center',
   alignItems: 'center',
   marginBottom: 24,
 },
 title: {
   fontSize: 28,
   fontWeight: '700',
   color: Colors.light.darkGreen,
   marginBottom: 8,
 },
 subtitle: {
   fontSize: 16,
   color: Colors.light.textLight,
 },
 formContainer: {
   width: '100%',
   marginBottom: 24,
 },
 inputContainer: {
   flexDirection: 'row',
   alignItems: 'center',
   borderWidth: 1,
   borderColor: Colors.light.border,
   borderRadius: 12,
   paddingHorizontal: 16,
   height: 56,
   marginBottom: 16,
 },
 inputIcon: {
   marginRight: 12,
 },
 input: {
   flex: 1,
   height: '100%',
   fontSize: 16,
   color: Colors.light.text,
 },
 eyeIcon: {
   padding: 8,
 },
 termsContainer: {
   flexDirection: 'row',
   alignItems: 'center',
   marginBottom: 24,
 },
 termsText: {
   fontSize: 14,
   color: Colors.light.textLight,
   marginLeft: 8,
 },
 termsLink: {
   color: Colors.light.darkGreen,
   fontWeight: '600',
 },
 registerButton: {
   height: 56,
   borderRadius: 12,
 },
 loginContainer: {
   flexDirection: 'row',
   justifyContent: 'center',
   alignItems: 'center',
   marginTop: 16,
 },
 loginText: {
   fontSize: 14,
   color: Colors.light.textLight,
   marginRight: 8,
 },
 loginButton: {
   padding: 4,
 },
 loginButtonText: {
   fontSize: 14,
   color: Colors.light.darkGreen,
   fontWeight: '600',
 },
});


components/AnimatedButton.tsx


import React from 'react';
import {
 StyleSheet,
 Text,
 TouchableOpacity,
 ActivityIndicator,
 StyleProp,
 ViewStyle,
 Platform,
} from 'react-native';
import Animated, { useSharedValue, useAnimatedStyle, withTiming, Easing } from 'react-native-reanimated';
import Colors from '@/constants/colors';


interface AnimatedButtonProps {
 title: string;
 onPress: () => void;
 style?: StyleProp<ViewStyle>;
 loading?: boolean;
 disabled?: boolean;
 solidColor?: string;
}


const AnimatedButton: React.FC<AnimatedButtonProps> = ({
 title,
 onPress,
 style,
 loading = false,
 disabled = false,
 solidColor
}) => {
 const scale = useSharedValue(1);
  const handlePressIn = () => {
   scale.value = withTiming(0.97, { duration: 100, easing: Easing.inOut(Easing.ease) });
 };
  const handlePressOut = () => {
   scale.value = withTiming(1, { duration: 200, easing: Easing.inOut(Easing.ease) });
 };
  const animatedStyle = useAnimatedStyle(() => {
   return {
     transform: [{ scale: scale.value }],
   };
 });


 // Use regular TouchableOpacity on web to avoid animation issues
 const AnimatedTouchable = Platform.OS === 'web'
   ? TouchableOpacity
   : Animated.createAnimatedComponent(TouchableOpacity);


 const isDisabled = disabled || loading;
 const buttonOpacity = isDisabled ? 0.7 : 1;
 const buttonColor = solidColor || Colors.light.primary; // Use the lighter green from colors.ts


 return (
   <AnimatedTouchable
     style={[
       styles.button,
       { backgroundColor: buttonColor, opacity: buttonOpacity },
       style,
       Platform.OS !== 'web' ? animatedStyle : {}
     ]}
     onPress={isDisabled ? undefined : onPress}
     onPressIn={handlePressIn}
     onPressOut={handlePressOut}
     activeOpacity={0.9}
     disabled={isDisabled}
   >
     {loading ? (
       <ActivityIndicator color="#FFFFFF" size="small" />
     ) : (
       <Text style={styles.buttonText}>{title}</Text>
     )}
   </AnimatedTouchable>
 );
};


const styles = StyleSheet.create({
 button: {
   height: 50,
   justifyContent: 'center',
   alignItems: 'center',
   borderRadius: 8,
 },
 buttonText: {
   color: '#FFFFFF',
   fontSize: 16,
   fontWeight: '600',
 },
});


export default AnimatedButton;


components/AnimatedCategoryCard.tsx


   width: categoryWidth,
   marginRight: 12,
   alignItems: 'center',
 },
 imageContainer: {
   width: categorySize,
   height: categorySize,
   borderRadius: categorySize / 2,
   overflow: 'hidden',
   marginBottom: 8,
   backgroundColor: '#F5F5F5',
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 4 },
   shadowOpacity: 0.15,
   shadowRadius: 8,
   elevation: 4,
   position: 'relative',
 },
 image: {
   width: '100%',
   height: '100%',
 },
 fallbackImageContainer: {
   ...StyleSheet.absoluteFillObject,
   justifyContent: 'center',
   alignItems: 'center',
   backgroundColor: Colors.light.primaryLight,
 },
 fallbackText: {
   fontSize: 24,
   fontWeight: '700',
   color: Colors.light.primary,
 },
 overlay: {
   ...StyleSheet.absoluteFillObject,
   backgroundColor: 'rgba(0, 0, 0, 0.1)',
 },
 name: {
   fontSize: width < 375 ? 12 : 14,
   color: Colors.light.text,
   textAlign: 'center',
   fontWeight: '500',
 }
});


components/AnimatedProductCard.tsx


           <View style={styles.featuredTag}>
             <Text style={styles.featuredText}>Featured</Text>
           </View>
         )}
       </View>
       <View style={styles.content}>
         <Text style={styles.name} numberOfLines={2}>{product.name}</Text>
         <Text style={styles.unit}>{product.unit}</Text>
         <View style={styles.footer}>
           <Text style={styles.price}>${product.price.toFixed(2)}</Text>
           <Pressable style={styles.addButton} onPress={handleAddToCart}>
             <Plus size={16} color="#FFFFFF" />
           </Pressable>
         </View>
       </View>
     </Pressable>
   </AnimatedContainer>
 );
}


const styles = StyleSheet.create({
 container: {
   backgroundColor: Colors.light.card,
   borderRadius: 16,
   overflow: 'hidden',
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 4 },
   shadowOpacity: 0.1,
   shadowRadius: 8,
   elevation: 3,
 },
 horizontalContainer: {
   flexDirection: 'row',
   width: '100%',
   height: 120,
 },
 imageWrapper: {
   position: 'relative',
   backgroundColor: '#F5F5F5',
 },
 image: {
   backgroundColor: '#F5F5F5',
 },
 verticalImage: {
   width: '100%',
   height: 140,
 },
 horizontalImage: {
   width: 120,
   height: '100%',
 },
 content: {
   padding: 12,
   flex: 1,
   justifyContent: 'space-between',
 },
 featuredTag: {
   position: 'absolute',
   top: 8,
   left: 8,
   backgroundColor: Colors.light.accent,
   paddingHorizontal: 8,
   paddingVertical: 2,
   borderRadius: 4,
 },
 featuredText: {
   color: '#FFFFFF',
   fontSize: 10,
   fontWeight: '600',
 },
 name: {
   fontSize: width < 375 ? 14 : 16,
   fontWeight: '600',
   color: Colors.light.text,
   marginBottom: 4,
 },
 unit: {
   fontSize: 12,
   color: Colors.light.textLight,
   marginBottom: 8,
 },
 footer: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
 },
 price: {
   fontSize: width < 375 ? 14 : 16,
   fontWeight: '700',
   color: Colors.light.text,
 },
 addButton: {
   width: 32,
   height: 32,
   borderRadius: 16,
   backgroundColor: Colors.light.primary,
   justifyContent: 'center',
   alignItems: 'center',
 },
});


components/Button.tsx


import React from 'react';
   switch (variant) {
     case 'primary':
     case 'secondary':
       textStyleObj.color = '#FFFFFF';
       break;
     case 'outline':
       textStyleObj.color = Colors.light.primary;
       break;
   }
    // Size text styles
   switch (size) {
     case 'small':
       textStyleObj.fontSize = width < 375 ? 12 : 14;
       break;
     case 'medium':
       textStyleObj.fontSize = width < 375 ? 14 : 16;
       break;
     case 'large':
       textStyleObj.fontSize = width < 375 ? 16 : 18;
       break;
   }
    return textStyleObj;
 };


 return (
   <Pressable
     style={[
       styles.button,
       getButtonStyle(),
       style
     ]}
     onPress={onPress}
     disabled={disabled || loading}
   >
     {loading ? (
       <ActivityIndicator
         color={variant === 'outline' ? Colors.light.primary : '#FFFFFF'}
         size="small"
       />
     ) : (
       <>
         {icon && icon}
         <Text style={[
           styles.text,
           getTextStyle(),
           icon && styles.textWithIcon,
           textStyle
         ]}>
           {title}
         </Text>
       </>
     )}
   </Pressable>
 );
}


const styles = StyleSheet.create({
 button: {
   borderRadius: 8,
   flexDirection: 'row',
   justifyContent: 'center',
   alignItems: 'center',
 },
 text: {
   fontWeight: '600',
   textAlign: 'center',
 },
 textWithIcon: {
   marginLeft: 8,
 },
});


components/CartIcon.tsx


import React, { useEffect } from 'react';
   <Pressable style={styles.container} onPress={handlePress} hitSlop={8}>
     <AnimatedView style={Platform.OS !== 'web' ? animatedStyle : {}}>
       <ShoppingBag size={iconSize} color={Colors.light.text} />
       {itemCount > 0 && (
         <AnimatedView
           style={[
             styles.badge,
             Platform.OS !== 'web' ? badgeAnimatedStyle : {}
           ]}
         >
           <Text style={styles.badgeText}>{itemCount > 99 ? '99+' : itemCount}</Text>
         </AnimatedView>
       )}
     </AnimatedView>
   </Pressable>
 );
}


const styles = StyleSheet.create({
 container: {
   marginRight: 15,
   position: 'relative',
 },
 badge: {
   position: 'absolute',
   top: -6,
   right: -8,
   backgroundColor: Colors.light.primary,
   borderRadius: 10,
   minWidth: 20,
   height: 20,
   justifyContent: 'center',
   alignItems: 'center',
   paddingHorizontal: 4,
 },
 badgeText: {
   color: '#FFFFFF',
   fontSize: 10,
   fontWeight: '700',
 },
});


components/CategoryCard.tsx


import React from 'react';
import { StyleSheet, Text, Pressable, View, Dimensions } from 'react-native';
import { Image } from 'expo-image';
import { useRouter } from 'expo-router';
import { Category } from '@/types';
import Colors from '@/constants/colors';


const { width } = Dimensions.get('window');
const categorySize = width < 375 ? 70 : 80;
const categoryWidth = width < 375 ? 90 : 100;


interface CategoryCardProps {
 category: Category;
}


export default function CategoryCard({ category }: CategoryCardProps) {
 const router = useRouter();


 const handlePress = () => {
   router.push(`/category/${category.id}`);
 };


 return (
   <Pressable style={styles.container} onPress={handlePress}>
     <View style={styles.imageContainer}>
       <Image
         source={{ uri: category.image }}
         style={styles.image}
         contentFit="cover"
         transition={200}
       />
       <View style={styles.overlay} />
     </View>
     <Text style={styles.name} numberOfLines={2}>{category.name}</Text>
   </Pressable>
 );
}


const styles = StyleSheet.create({
 container: {
   width: categoryWidth,
   marginRight: 12,
   alignItems: 'center',
 },
 imageContainer: {
   width: categorySize,
   height: categorySize,
   borderRadius: categorySize / 2,
   overflow: 'hidden',
   marginBottom: 8,
   backgroundColor: '#E1E1E1',
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 4 },
   shadowOpacity: 0.15,
   shadowRadius: 8,
   elevation: 4,
   position: 'relative',
 },
 image: {
   width: '100%',
   height: '100%',
 },
 overlay: {
   ...StyleSheet.absoluteFillObject,
   backgroundColor: 'rgba(0, 0, 0, 0.1)',
 },
 name: {
   fontSize: width < 375 ? 12 : 14,
   color: Colors.light.text,
   textAlign: 'center',
   fontWeight: '500',
 }
});


components/EmptyState.tsx


import React from 'react';
import { StyleSheet, Text, View, Dimensions } from 'react-native';
import Colors from '@/constants/colors';
import Button from './Button';


const { width } = Dimensions.get('window');


interface EmptyStateProps {
 icon: React.ReactNode;
 title: string;
 message: string;
 buttonTitle?: string;
 onButtonPress?: () => void;
}


export default function EmptyState({
 icon,
 title,
 message,
 buttonTitle,
 onButtonPress
}: EmptyStateProps) {
 return (
   <View style={styles.container}>
     <View style={styles.iconContainer}>
       {icon}
     </View>
     <Text style={styles.title}>{title}</Text>
     <Text style={styles.message}>{message}</Text>
    
     {buttonTitle && onButtonPress && (
       <Button
         title={buttonTitle}
         onPress={onButtonPress}
         style={styles.button}
       />
     )}
   </View>
 );
}


const styles = StyleSheet.create({
 container: {
   flex: 1,
   justifyContent: 'center',
   alignItems: 'center',
   padding: 24,
   minHeight: 300,
 },
 iconContainer: {
   width: width < 375 ? 70 : 80,
   height: width < 375 ? 70 : 80,
   borderRadius: width < 375 ? 35 : 40,
   backgroundColor: 'rgba(76, 175, 80, 0.1)',
   justifyContent: 'center',
   alignItems: 'center',
   marginBottom: 24,
 },
 title: {
   fontSize: width < 375 ? 18 : 20,
   fontWeight: '700',
   color: Colors.light.text,
   marginBottom: 8,
   textAlign: 'center',
 },
 message: {
   fontSize: width < 375 ? 14 : 16,
   color: Colors.light.textLight,
   textAlign: 'center',
   marginBottom: 24,
 },
 button: {
   minWidth: width < 375 ? 180 : 200,
 },
});


components/ImpactCard.tsx


import React, { useEffect } from 'react';
import { StyleSheet, Text, View, Dimensions } from 'react-native';
import { Leaf, Droplets, Wind } from 'lucide-react-native';
import Animated, { useSharedValue, useAnimatedStyle, withTiming, withDelay, withSpring } from 'react-native-reanimated';
import { Platform } from 'react-native';
import Colors from '@/constants/colors';


const { width } = Dimensions.get('window');
const iconSize = width < 375 ? 20 : 24;
const containerSize = width < 375 ? 40 : 48;


interface ImpactCardProps {
 title: string;
 value: number;
 unit: string;
 type: 'food' | 'water' | 'carbon';
 index?: number;
}


export default function ImpactCard({ title, value, unit, type, index = 0 }: ImpactCardProps) {
 const scale = useSharedValue(0.8);
 const opacity = useSharedValue(0);
 const translateY = useSharedValue(20);


 useEffect(() => {
   // Staggered animation based on index
   const delay = index * 150;
  
   scale.value = withDelay(
     delay,
     withSpring(1, { damping: 12, stiffness: 100 })
   );
  
   opacity.value = withDelay(
     delay,
     withTiming(1, { duration: 500 })
   );
  
   translateY.value = withDelay(
     delay,
     withTiming(0, { duration: 500 })
   );
 }, []);


 const animatedStyle = useAnimatedStyle(() => {
   return {
     opacity: opacity.value,
     transform: [
       { scale: scale.value },
       { translateY: translateY.value }
     ]
   };
 });


 const renderIcon = () => {
   switch (type) {
     case 'food':
       return <Leaf size={iconSize} color={Colors.light.primary} />;
     case 'water':
       return <Droplets size={iconSize} color="#2196F3" />;
     case 'carbon':
       return <Wind size={iconSize} color="#607D8B" />;
     default:
       return null;
   }
 };


 // Use regular View on web to avoid layout animation issues
 const AnimatedView = Platform.OS === 'web' ? View : Animated.View;


 return (
   <AnimatedView
     style={[
       styles.container,
       Platform.OS !== 'web' ? animatedStyle : {}
     ]}
   >
     <View style={styles.iconContainer}>
       {renderIcon()}
     </View>
     <Text style={styles.title}>{title}</Text>
     <Text style={styles.value}>
       {value.toLocaleString(undefined, { maximumFractionDigits: 1 })} {unit}
     </Text>
   </AnimatedView>
 );
}


const styles = StyleSheet.create({
 container: {
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   padding: 16,
   alignItems: 'center',
   flex: 1,
   minWidth: 100,
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 2 },
   shadowOpacity: 0.1,
   shadowRadius: 4,
   elevation: 2,
 },
 iconContainer: {
   width: containerSize,
   height: containerSize,
   borderRadius: containerSize / 2,
   backgroundColor: 'rgba(76, 175, 80, 0.1)',
   justifyContent: 'center',
   alignItems: 'center',
   marginBottom: 12,
 },
 title: {
   fontSize: width < 375 ? 12 : 14,
   color: Colors.light.textLight,
   marginBottom: 4,
   textAlign: 'center',
 },
 value: {
   fontSize: width < 375 ? 16 : 18,
   fontWeight: '700',
   color: Colors.light.text,
   textAlign: 'center',
 },
});


components/QuantitySelector.tsx


import React from 'react';
     onDecrease();
   }
 };


 const increaseAnimatedStyle = useAnimatedStyle(() => {
   return {
     transform: [{ scale: scaleIncrease.value }]
   };
 });


 const decreaseAnimatedStyle = useAnimatedStyle(() => {
   return {
     transform: [{ scale: scaleDecrease.value }]
   };
 });


 const quantityAnimatedStyle = useAnimatedStyle(() => {
   return {
     transform: [{ scale: scaleQuantity.value }]
   };
 });


 // Use regular View on web to avoid layout animation issues
 const AnimatedPressable = Platform.OS === 'web' ? Pressable : Animated.createAnimatedComponent(Pressable);
 const AnimatedText = Platform.OS === 'web' ? Text : Animated.createAnimatedComponent(Text);


 return (
   <View style={styles.container}>
     <AnimatedPressable
       style={[
         styles.button,
         quantity <= minQuantity && styles.disabledButton,
         Platform.OS !== 'web' ? decreaseAnimatedStyle : {}
       ]}
       onPress={handleDecrease}
       disabled={quantity <= minQuantity}
     >
       <Minus
         size={iconSize}
         color={quantity <= minQuantity ? Colors.light.textLight : Colors.light.text}
       />
     </AnimatedPressable>
    
     <AnimatedText
       style={[
         styles.quantity,
         Platform.OS !== 'web' ? quantityAnimatedStyle : {}
       ]}
     >
       {quantity}
     </AnimatedText>
    
     <AnimatedPressable
       style={[
         styles.button,
         Platform.OS !== 'web' ? increaseAnimatedStyle : {}
       ]}
       onPress={handleIncrease}
     >
       <Plus size={iconSize} color={Colors.light.text} />
     </AnimatedPressable>
   </View>
 );
}


const styles = StyleSheet.create({
 container: {
   flexDirection: 'row',
   alignItems: 'center',
   borderWidth: 1,
   borderColor: Colors.light.border,
   borderRadius: 8,
   overflow: 'hidden',
 },
 button: {
   width: buttonSize,
   height: buttonSize,
   justifyContent: 'center',
   alignItems: 'center',
   backgroundColor: Colors.light.card,
 },
 disabledButton: {
   opacity: 0.5,
 },
 quantity: {
   width: buttonSize,
   textAlign: 'center',
   fontSize: width < 375 ? 14 : 16,
   fontWeight: '600',
   color: Colors.light.text,
 },
});


components/SkeletonLoader.tsx


import React from 'react';
import { View, StyleSheet, Dimensions } from 'react-native';
import Colors from '@/constants/colors';


const { width } = Dimensions.get('window');


interface SkeletonProps {
 width?: number | string;
 height?: number;
 borderRadius?: number;
 style?: any;
}


export default function SkeletonLoader({
 width: propWidth = '100%',
 height = 20,
 borderRadius = 4,
 style
}: SkeletonProps) {
 return (
   <View
     style={[
       styles.skeleton,
       { width: propWidth, height, borderRadius, opacity: 0.3 },
       style
     ]}
   />
 );
}


// Product Card Skeleton
export function ProductCardSkeleton({ horizontal = false }) {
 return (
   <View style={[
     styles.card,
     horizontal ? styles.horizontalCard : styles.verticalCard
   ]}>
     <SkeletonLoader
       height={horizontal ? 120 : 120}
       width={horizontal ? 120 : '100%'}
       borderRadius={0}
     />
     <View style={styles.cardContent}>
       <SkeletonLoader width="70%" height={16} style={{ marginBottom: 8 }} />
       <SkeletonLoader width="40%" height={12} style={{ marginBottom: 12 }} />
       <View style={styles.cardFooter}>
         <SkeletonLoader width={50} height={16} />
         <SkeletonLoader width={28} height={28} borderRadius={14} />
       </View>
     </View>
   </View>
 );
}


// Category Card Skeleton
export function CategoryCardSkeleton() {
 const size = width < 375 ? 70 : 80;
 return (
   <View style={styles.categoryCard}>
     <SkeletonLoader
       width={size}
       height={size}
       borderRadius={size / 2}
       style={{ marginBottom: 8 }}
     />
     <SkeletonLoader width={60} height={14} style={{ alignSelf: 'center' }} />
   </View>
 );
}


const styles = StyleSheet.create({
 skeleton: {
   backgroundColor: Colors.light.border,
 },
 card: {
   backgroundColor: Colors.light.card,
   borderRadius: 12,
   overflow: 'hidden',
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 2 },
   shadowOpacity: 0.1,
   shadowRadius: 4,
   elevation: 2,
 },
 verticalCard: {
   width: '100%',
   height: width < 375 ? 200 : 220,
 },
 horizontalCard: {
   flexDirection: 'row',
   width: '100%',
   height: 120,
 },
 cardContent: {
   padding: 12,
   flex: 1,
   justifyContent: 'space-between',
 },
 cardFooter: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
 },
 categoryCard: {
   width: width < 375 ? 90 : 100,
   marginRight: 12,
   alignItems: 'center',
 },
});


components/SubscriptionCard.tsx


import { Image } from 'expo-image';
   marginBottom: 16,
   shadowColor: '#000',
   shadowOffset: { width: 0, height: 2 },
   shadowOpacity: 0.1,
   shadowRadius: 4,
   elevation: 2,
 },
 imageContainer: {
   width: 100,
   height: 120,
 },
 image: {
   width: '100%',
   height: '100%',
   backgroundColor: '#E1E1E1',
 },
 content: {
   padding: 12,
   flex: 1,
 },
 header: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   marginBottom: 8,
 },
 name: {
   fontSize: 16,
   fontWeight: '600',
   color: Colors.light.text,
   flex: 1,
 },
 statusBadge: {
   paddingHorizontal: 8,
   paddingVertical: 4,
   borderRadius: 4,
 },
 activeBadge: {
   backgroundColor: 'rgba(76, 175, 80, 0.1)',
 },
 inactiveBadge: {
   backgroundColor: 'rgba(158, 158, 158, 0.1)',
 },
 statusText: {
   fontSize: 12,
   fontWeight: '600',
 },
 activeText: {
   color: Colors.light.primary,
 },
 inactiveText: {
   color: Colors.light.textLight,
 },
 infoRow: {
   flexDirection: 'row',
   alignItems: 'center',
   marginBottom: 8,
 },
 infoText: {
   fontSize: 14,
   color: Colors.light.textLight,
   marginLeft: 8,
 },
 footer: {
   flexDirection: 'row',
   justifyContent: 'space-between',
   alignItems: 'center',
   marginTop: 8,
 },
 price: {
   fontSize: 18,
   fontWeight: '700',
   color: Colors.light.text,
 },
});


constants/colors.ts


const tintColorLight = '#4CAF50';  // Lighter green
const tintColorDark = '#66BB6A';   // Lighter green for dark mode


export default {
 light: {
   text: '#1A1A1A',
   textLight: '#666666',
   background: '#FFFFFF',
   backgroundAlt: '#F8FAF8',
   card: '#FFFFFF',
   cardAlt: '#F5F7F5',
   border: '#E0E0E0',
   borderLight: '#F0F0F0',
   tint: tintColorLight,
   tabIconDefault: '#CCCCCC',
   tabIconSelected: tintColorLight,
  
   // Green shades - lighter palette
   primary: '#4CAF50',        // Lighter rich green (was #2E7D32)
   primaryLight: '#A5D6A7',   // Light green
   darkGreen: '#388E3C',      // Lighter dark green (was #1B5E20)
   lightGreen: '#81C784',     // Light green
   mintGreen: '#C8E6C9',      // Very light mint green
   oliveGreen: '#689F38',     // Lighter olive green (was #558B2F)
   emeraldGreen: '#00E676',   // Brighter emerald green (was #00C853)
   forestGreen: '#43A047',    // Lighter forest green (was #2D6A4F)
   sageGreen: '#8BC34A',      // Lighter sage green (was #7CB342)
  
   // Accent colors - warmer, more premium
   accent: '#E67E22',         // Warm orange accent
   accentLight: '#FFCCBC',    // Light orange
  
   // Status colors
   success: '#4CAF50',
   warning: '#FFC107',
   error: '#F44336',
   info: '#2196F3',
 },
 dark: {
   text: '#FFFFFF',
   textLight: '#BBBBBB',
   background: '#121212',
   backgroundAlt: '#1E1E1E',
   card: '#1E1E1E',
   cardAlt: '#2C2C2C',
   border: '#333333',
   borderLight: '#444444',
   tint: tintColorDark,
   tabIconDefault: '#666666',
   tabIconSelected: tintColorDark,
  
   // Green shades - lighter
   primary: '#66BB6A',        // Lighter green for dark mode (was #4CAF50)
   primaryLight: '#A5D6A7',
   darkGreen: '#43A047',      // Lighter dark green (was #2E7D32)
   lightGreen: '#81C784',
   mintGreen: '#C8E6C9',
   oliveGreen: '#7CB342',     // Lighter olive (was #689F38)
   emeraldGreen: '#00E676',   // Brighter emerald (was #00C853)
   forestGreen: '#43A047',    // Lighter forest (was #2D6A4F)
   sageGreen: '#8BC34A',      // Lighter sage (was #7CB342)
  
   // Accent colors
   accent: '#E67E22',
   accentLight: '#FFCCBC',
  
   // Status colors
   success: '#4CAF50',
   warning: '#FFC107',
   error: '#F44336',
   info: '#2196F3',
 },
};


mocks/categories.ts


import { Category } from "@/types";


export const categories: Category[] = [
 {
   id: "vegetables",
   name: "Pre-Cut Vegetables",
   image: "https://images.unsplash.com/photo-1540420773420-3366772f4999?q=80&w=2084&auto=format&fit=crop",
   description: "Fresh, pre-cut vegetables that save time and reduce waste."
 },
 {
   id: "ready-meals",
   name: "Ready Meals",
   image: "https://images.unsplash.com/photo-1546069901-ba9599a7e63c?q=80&w=2080&auto=format&fit=crop",
   description: "Delicious, ready-to-eat meals made with fresh ingredients."
 },
 {
   id: "meal-kits",
   name: "Meal Kits",
   image: "https://images.unsplash.com/photo-1543362906-acfc16c67564?q=80&w=2091&auto=format&fit=crop",
   description: "Everything you need to make a delicious meal at home."
 },
 {
   id: "indian",
   name: "Indian Cuisine",
   image: "https://images.unsplash.com/photo-1585937421612-70a008356c36?q=80&w=2036&auto=format&fit=crop",
   description: "Authentic Indian flavors made easy with pre-prepped ingredients."
 },
 {
   id: "bundles",
   name: "Bundles & Kits",
   image: "https://images.unsplash.com/photo-1610348725531-843dff563e2c?q=80&w=2070&auto=format&fit=crop",
   description: "Curated collections of our most popular products."
 }
];


mocks/products.ts


import { Product } from "@/types";
   unit: "3 oz jar",
   inStock: true,
   nutritionFacts: {
     calories: 10,
     protein: 0,
     carbs: 2,
     fat: 0
   },
   carbonFootprint: 0.4,
   waterSaved: 15
 },
 {
   id: "26",
   name: "Vegetable Curry Kit",
   description: "Make a delicious vegetable curry with pre-cut vegetables, authentic spice blend, and coconut milk.",
   price: 9.99,  // Reduced from 12.99
   image: "https://images.unsplash.com/photo-1604152135912-04a022e23696?q=80&w=2069&auto=format&fit=crop",
   category: "indian",
   tags: ["meal-kit", "vegan", "indian"],
   unit: "26 oz kit (serves 2)",
   inStock: true,
   nutritionFacts: {
     calories: 380,
     protein: 10,
     carbs: 45,
     fat: 18
   },
   carbonFootprint: 1.6,
   waterSaved: 45
 },
 // Bundles
 {
   id: "13",
   name: "Weekly Essentials Bundle",
   description: "A curated selection of our most popular pre-cut vegetables for everyday cooking.",
   price: 14.99,  // Reduced from 19.99
   image: "https://images.unsplash.com/photo-1610348725531-843dff563e2c?q=80&w=2070&auto=format&fit=crop",
   category: "bundles",
   tags: ["bundle", "essentials", "vegetables"],
   unit: "5 items (approx. 3 lbs)",
   inStock: true,
   isFeatured: true,
   carbonFootprint: 3.5,
   waterSaved: 90
 },
 {
   id: "14",
   name: "Meal Prep Starter Bundle",
   description: "Everything you need for efficient meal prepping: pre-cut proteins and vegetables.",
   price: 18.99,  // Reduced from 24.99
   image: "https://images.unsplash.com/photo-1498837167922-ddd27525d352?q=80&w=2070&auto=format&fit=crop",
   category: "bundles",
   tags: ["bundle", "meal-prep", "variety"],
   unit: "6 items (approx. 4 lbs)",
   inStock: true,
   carbonFootprint: 4.2,
   waterSaved: 110
 },
 {
   id: "15",
   name: "Low-Carb Bundle",
   description: "A selection of low-carb vegetable alternatives including cauliflower rice and zucchini noodles.",
   price: 16.99,  // Reduced from 22.99
   image: "https://images.unsplash.com/photo-1467453678174-768ec283a940?q=80&w=2144&auto=format&fit=crop",
   category: "bundles",
   tags: ["bundle", "low-carb", "keto-friendly"],
   unit: "4 items (approx. 2.5 lbs)",
   inStock: true,
   carbonFootprint: 2.8,
   waterSaved: 75
 },
 {
   id: "16",
   name: "Family Dinner Bundle",
   description: "A week's worth of pre-prepped ingredients for family dinners, saving you time and reducing waste.",
   price: 29.99,  // Reduced from 39.99
   image: "https://images.unsplash.com/photo-1547592166-23ac45744acd?q=80&w=2071&auto=format&fit=crop",
   category: "bundles",
   tags: ["bundle", "family", "meal-planning"],
   unit: "8 items (approx. 6 lbs)",
   inStock: true,
   carbonFootprint: 6.5,
   waterSaved: 180
 },
 {
   id: "27",
   name: "Indian Cuisine Bundle",
   description: "Explore authentic Indian flavors with this bundle including curry kits, spice blends, and ready meals.",
   price: 24.99,  // Reduced from 34.99
   image: "https://images.unsplash.com/photo-1596797038530-2c107aa8e1fa?q=80&w=2070&auto=format&fit=crop",
   category: "bundles",
   tags: ["bundle", "indian", "variety"],
   unit: "5 items",
   inStock: true,
   carbonFootprint: 4.0,
   waterSaved: 95
 }
];


mocks/subscriptions.ts


import { Subscription } from "@/types";


// Empty default subscriptions array - users will create their own
export const subscriptions: Subscription[] = [];


store/cart-store.ts


import { create } from 'zustand';
import { persist, createJSONStorage } from 'zustand/middleware';
import AsyncStorage from '@react-native-async-storage/async-storage';
import { CartItem, Product } from '@/types';


interface CartState {
 items: CartItem[];
 addItem: (product: Product, quantity: number) => void;
 removeItem: (productId: string) => void;
 updateQuantity: (productId: string, quantity: number) => void;
 clearCart: () => void;
 getTotal: () => number;
 getItemCount: () => number;
}


export const useCartStore = create<CartState>()(
 persist(
   (set, get) => ({
     items: [],
    
     addItem: (product: Product, quantity: number) => {
       set((state) => {
         const existingItem = state.items.find(item => item.product.id === product.id);
        
         if (existingItem) {
           return {
             items: state.items.map(item =>
               item.product.id === product.id
                 ? { ...item, quantity: item.quantity + quantity }
                 : item
             )
           };
         } else {
           return {
             items: [...state.items, { product, quantity }]
           };
         }
       });
     },
    
     removeItem: (productId: string) => {
       set((state) => ({
         items: state.items.filter(item => item.product.id !== productId)
       }));
     },
    
     updateQuantity: (productId: string, quantity: number) => {
       set((state) => ({
         items: state.items.map(item =>
           item.product.id === productId
             ? { ...item, quantity }
             : item
         )
       }));
     },
    
     clearCart: () => {
       set({ items: [] });
     },
    
     getTotal: () => {
       return get().items.reduce(
         (total, item) => total + (item.product.price * item.quantity),
         0
       );
     },
    
     getItemCount: () => {
       return get().items.reduce((count, item) => count + item.quantity, 0);
     }
   }),
   {
     name: 'cart-storage',
     storage: createJSONStorage(() => AsyncStorage)
   }
 )
);


store/user-store.ts


import { create } from 'zustand';
         } : null
       }));
     },
    
     addSubscription: (subscription: Subscription) => {
       set((state) => ({
         subscriptions: [subscription, ...state.subscriptions]
       }));
     },
    
     updateSubscription: (id: string, isActive: boolean) => {
       set((state) => ({
         subscriptions: state.subscriptions.map(sub =>
           sub.id === id ? { ...sub, isActive } : sub
         )
       }));
     },
    
     deleteSubscription: (id: string) => {
       set((state) => ({
         subscriptions: state.subscriptions.filter(sub => sub.id !== id)
       }));
     },
    
     logout: () => {
       set({
         user: defaultUser,
         isLoggedIn: false,
         orders: [],
         subscriptions: []
       });
     },
    
     updateImpactStats: (foodSaved: number, carbonReduced: number, waterSaved: number) => {
       set((state) => ({
         user: state.user ? {
           ...state.user,
           impactStats: {
             ...state.user.impactStats,
             foodWasteSaved: state.user.impactStats.foodWasteSaved + foodSaved,
             carbonFootprintReduced: state.user.impactStats.carbonFootprintReduced + carbonReduced,
             waterSaved: state.user.impactStats.waterSaved + waterSaved
           }
         } : null
       }));
     },
    
     updateNotificationPreferences: (preferences: NotificationPreferences) => {
       set((state) => ({
         user: state.user ? {
           ...state.user,
           notificationPreferences: preferences
         } : null
       }));
     },
    
     updatePaymentMethods: (paymentMethods) => {
       set((state) => ({
         user: state.user ? {
           ...state.user,
           paymentMethods
         } : null
       }));
     }
   }),
   {
     name: 'user-storage',
     storage: createJSONStorage(() => AsyncStorage)
   }
 )
);


types/index.ts


export interface User {
 name: string;
 email: string;
 address: string;
 phone: string;
 photoUrl?: string;
 impactStats: {
   foodWasteSaved: number;
   carbonFootprintReduced: number;
   waterSaved: number;
   ordersPlaced: number;
 };
 notificationPreferences: NotificationPreferences;
 paymentMethods?: any[];
}


export interface NotificationPreferences {
 orderUpdates: boolean;
 promotions: boolean;
 subscriptionReminders: boolean;
}


export interface Product {
 id: string;
 name: string;
 description: string;
 price: number;
 image: string;
 category: string;
 tags: string[];
 unit: string;
 inStock: boolean;
 isFeatured?: boolean;
 nutritionFacts?: {
   calories: number;
   protein: number;
   carbs: number;
   fat: number;
 };
 carbonFootprint?: number;
 waterSaved?: number;
}


export interface CartItem {
 product: Product;
 quantity: number;
}


export interface Order {
 id: string;
 items: CartItem[];
 total: number;
 date: string;
 status: 'processing' | 'shipped' | 'delivered' | 'cancelled';
 deliveryAddress: string;
 deliveryDate: string;
 paymentMethod: string;
 deliveryOption: string;
}


export interface Subscription {
 id: string;
 name: string;
 description: string;
 items: CartItem[];
 frequency: 'weekly' | 'biweekly' | 'monthly';
 nextDelivery: string;
 price: number;
 isActive: boolean;
 createdAt: string;
}


export interface Category {
 id: string;
 name: string;
 image: string;
 description: string;
}


.gitignore


# Learn more https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files


# dependencies
node_modules/


# Expo
.expo/
dist/
web-build/
expo-env.d.ts


# Native
*.orig.*
*.jks
*.p8
*.p12
*.key
*.mobileprovision


# Metro
.metro-health-check*


# debug
npm-debug.*
yarn-debug.*
yarn-error.*


# macOS
.DS_Store
*.pem


# local env files
.env*.local


# typescript
*.tsbuildinfo
.vercel


app.json




{
 "expo": {
   "name": "freshprep veggies",
   "slug": "eco-friendly-food-subscription-app",
   "version": "1.0.0",
   "orientation": "portrait",
   "icon": "./assets/images/icon.png",
   "scheme": "myapp",
   "userInterfaceStyle": "automatic",
   "splash": {
     "image": "./assets/images/splash-icon.png",
     "resizeMode": "contain",
     "backgroundColor": "#ffffff"
   },
   "ios": {
     "supportsTablet": true,
     "bundleIdentifier": "app.rork.freshprep-veggies"
   },
   "android": {
     "adaptiveIcon": {
       "foregroundImage": "./assets/images/adaptive-icon.png",
       "backgroundColor": "#ffffff"
     },
     "package": "app.rork.freshprep-veggies"
   },
   "web": {
     "favicon": "./assets/images/favicon.png"
   },
   "plugins": [
     "expo-router",
     [
       "expo-notifications",
       {
         "icon": "./assets/images/notification-icon.png",
         "color": "#4CAF50",
         "sounds": ["./assets/sounds/notification.wav"]
       }
     ]
   ],
   "experiments": {
     "typedRoutes": true
   }
 }
}


bun.lock


       "@react-native-async-storage/async-storage": "2.1.2",


   "@isaacs/cliui/wrap-ansi/ansi-styles": ["ansi-styles@6.2.1", "", {}, "sha512-bN798gFfQX+viw3R7yrGWRqnrN2oRkEkUjjl4JNn4E8GxxbjtG3FbrEIIY3l8/hrwUwIeCZvi4QuOTP4MErVug=="],


   "@istanbuljs/load-nyc-config/find-up/locate-path": ["locate-path@5.0.0", "", { "dependencies": { "p-locate": "^4.1.0" } }, "sha512-t7hw9pI+WvuwNJXwk5zVHpyhIqzg2qTlklJOf0mVxGSbe3Fp2VieZcduNYjaLDoy6p9uGpQEGWG87WpMKlNq8g=="],


   "@istanbuljs/load-nyc-config/js-yaml/argparse": ["argparse@1.0.10", "", { "dependencies": { "sprintf-js": "~1.0.2" } }, "sha512-o5Roy6tNG4SL/FOkCAN6RzjiakZS25RLYFrcMttJqbdd8BWrnA+fGz57iN5Pb06pvBGvl5gQ0B48dJlslXvoTg=="],


   "@react-native/community-cli-plugin/debug/ms": ["ms@2.0.0", "", {}, "sha512-Tpp60P6IUJDTuOq/5Z8cdskzJujfwqfOTkrwIwj7IRISpnkJnT6SyJ4PCPnGMoFjC9ddhal5KVIYtAt97ix05A=="],


   "@react-native/dev-middleware/debug/ms": ["ms@2.0.0", "", {}, "sha512-Tpp60P6IUJDTuOq/5Z8cdskzJujfwqfOTkrwIwj7IRISpnkJnT6SyJ4PCPnGMoFjC9ddhal5KVIYtAt97ix05A=="],


   "compression/debug/ms": ["ms@2.0.0", "", {}, "sha512-Tpp60P6IUJDTuOq/5Z8cdskzJujfwqfOTkrwIwj7IRISpnkJnT6SyJ4PCPnGMoFjC9ddhal5KVIYtAt97ix05A=="],


   "connect/debug/ms": ["ms@2.0.0", "", {}, "sha512-Tpp60P6IUJDTuOq/5Z8cdskzJujfwqfOTkrwIwj7IRISpnkJnT6SyJ4PCPnGMoFjC9ddhal5KVIYtAt97ix05A=="],


   "cosmiconfig/js-yaml/argparse": ["argparse@1.0.10", "", { "dependencies": { "sprintf-js": "~1.0.2" } }, "sha512-o5Roy6tNG4SL/FOkCAN6RzjiakZS25RLYFrcMttJqbdd8BWrnA+fGz57iN5Pb06pvBGvl5gQ0B48dJlslXvoTg=="],


   "finalhandler/debug/ms": ["ms@2.0.0", "", {}, "sha512-Tpp60P6IUJDTuOq/5Z8cdskzJujfwqfOTkrwIwj7IRISpnkJnT6SyJ4PCPnGMoFjC9ddhal5KVIYtAt97ix05A=="],


   "glob/minimatch/brace-expansion": ["brace-expansion@1.1.11", "", { "dependencies": { "balanced-match": "^1.0.0", "concat-map": "0.0.1" } }, "sha512-iCuPHDFgrHX7H2vEI/5xpz07zSHB00TpugqhmYtVmMO6518mCuRMoOYFldEBl0g187ufozdaHgWKcYFb61qGiA=="],


   "lighthouse-logger/debug/ms": ["ms@2.0.0", "", {}, "sha512-Tpp60P6IUJDTuOq/5Z8cdskzJujfwqfOTkrwIwj7IRISpnkJnT6SyJ4PCPnGMoFjC9ddhal5KVIYtAt97ix05A=="],


package.json
{
 "name": "expo-app",
 "main": "expo-router/entry",
 "version": "1.0.0",
 "scripts": {
   "start": "expo start --tunnel",
   "start-web": "expo start --web --tunnel",
   "start-web-dev": "DEBUG=expo* expo start --web --tunnel"
 },
 "dependencies": {
   "@expo/vector-icons": "^14.1.0",
   "@react-native-async-storage/async-storage": "2.1.2",
   "@react-navigation/native": "^7.1.6",
   "expo": "^53.0.4",
   "expo-auth-session": "~6.1.5",
   "expo-blur": "~14.1.4",
   "expo-constants": "~17.1.4",
   "expo-font": "~13.3.0",
   "expo-haptics": "~14.1.4",
   "expo-image": "~2.1.6",
   "expo-image-picker": "~16.1.4",
   "expo-linear-gradient": "~14.1.4",
   "expo-linking": "~7.1.4",
   "expo-location": "~18.1.4",
   "expo-notifications": "~0.31.1",
   "expo-router": "~5.0.3",
   "expo-splash-screen": "~0.30.7",
   "expo-status-bar": "~2.2.3",
   "expo-symbols": "~0.4.4",
   "expo-system-ui": "~5.0.6",
   "expo-web-browser": "~14.1.6",
   "lucide-react-native": "^0.475.0",
   "nativewind": "^4.1.23",
   "react": "19.0.0",
   "react-dom": "19.0.0",
   "react-native": "0.79.1",
   "react-native-gesture-handler": "~2.24.0",
   "react-native-reanimated": "~3.17.4",
   "react-native-safe-area-context": "5.3.0",
   "react-native-screens": "~4.10.0",
   "react-native-svg": "15.11.2",
   "react-native-web": "^0.20.0",
   "zustand": "^5.0.2"
 },
 "devDependencies": {
   "@babel/core": "^7.25.2",
   "@expo/ngrok": "^4.1.0",
   "@types/react": "~19.0.10",
   "typescript": "~5.8.3"
 },
 "private": true
}


tsconfig.json
{
 "extends": "expo/tsconfig.base",
 "compilerOptions": {
   "strict": true,
   "paths": {
     "@/*": [
       "./*"
     ]
   }
 },
 "include": [
   "**/*.ts",
   "**/*.tsx",
   ".expo/types/**/*.ts",
   "expo-env.d.ts"
 ]
}


vercel.json


{
 "buildCommand": "expo export -p web",
 "outputDirectory": "dist",
 "devCommand": "expo",
 "cleanUrls": true,
 "framework": null,
 "rewrites": [
   {
     "source": "/:path*",
     "destination": "/"
   }
 ]
}








